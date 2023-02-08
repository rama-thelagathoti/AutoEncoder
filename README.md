Implementation of convolutional Autoencoder for CIFAR-10 
---------------------------------------------------------
Introduction

Autoencoder is special type of neural network where the input is same as the output. The main objective of this assignment is to design and develop convolutional autoencoder for CIFAR-10 dataset. The dataset consists of 60,000 images in 10 different classes namely airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships, and trucks. Each class contains 6000 images. All the images are of size 32x32 with three (R, G, B) channels. 
Cifar-10 dataset has Input images of dimension 32x32 with RGB (3) channels. The encoder is designed to compress the image by extracting the important features. It contains a stack of Conv2D and MaxPooling2D layers to perform 2D convolution and down sampling. Whereas the decoder component utilizes the compressed image and extracts the original image. However, as autoencoders are lossy approach there will be a compromise on accuracy metric.  
Since, the encoder component contains Maxpool2D layer which might down sample the data by reducing the number of bits used for representation.  I have tested two methods by defining the compression ratio. In case 1 (described in Results section), input image is compressed by 1/16 and decoded from the compressed image. Whereas, in case 2 (shown below), input image is compressed by 1/8 then obtained original image from the encoded image.  From the results it is observed that lesser the compression ration higher the accuracy. For case 2, workflow is depicted in following figure. Summary results are shown in the following table. 
![Picture4](https://user-images.githubusercontent.com/36952323/217412100-7daaffaa-d72f-4f00-9648-57783fae8261.png)

Method

Before constructing an autoencoder pipeline, it is essential to preprocess the data. Preprocessing includes data normalization to achieve high accuracy. The input image has 3 channel color data, and each data point ranges between 0 to 255. Hence, to normalize the data each data point is converted to float type and then divided by 255. The resultant normalized data has the values ranges between o and 1. 
Following figure describes the autoencoder pipeline that is designed to perform the encoding of the input image as well decoding from encoded image.


![Picture2](https://user-images.githubusercontent.com/36952323/217411638-9219dcc1-817a-4a5b-aeaa-87900c1110ea.png)

Results

I have considered default training and test parameters that I obtained during cifar-10 dataset loading which is as follows
train data (50000, 32, 32, 3)
test data (10000, 32, 32, 3)
Then I have trained the model with following parameters
epochs = 100
batch_size = 50
optimizer = 'adam'
loss ='mse'

The designed autoencoder pipeline achieved ~65% accuracy while the loss is 0.0154

Input image and decoded images are shown below

 ![Picture3](https://user-images.githubusercontent.com/36952323/217412214-ce1c5c0c-b534-4f24-8f79-b45fb5cf13a6.png)


accuracy and loss metrics described below

 
![Picture5](https://user-images.githubusercontent.com/36952323/217412360-811b133a-b5f2-4cfa-a670-9fe380beef0d.png)


