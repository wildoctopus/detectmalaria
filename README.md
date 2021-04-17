# Detect Malaria
Classify the microscopy Images into Malaria and No_Malaria using Tensorflow2.X



## Model Architecture

    Model: "sequential_1"
    _________________________________________________________________
    Layer (type)                 Output Shape              Param #   
    =================================================================
    sequential (Sequential)      (None, 40, 40, 3)         0         
    _________________________________________________________________
    rescaling (Rescaling)        (None, 40, 40, 3)         0         
    _________________________________________________________________
    conv2d (Conv2D)              (None, 38, 38, 32)        896       
    _________________________________________________________________
    max_pooling2d (MaxPooling2D) (None, 19, 19, 32)        0         
    _________________________________________________________________
    conv2d_1 (Conv2D)            (None, 17, 17, 64)        18496     
    _________________________________________________________________
    max_pooling2d_1 (MaxPooling2 (None, 8, 8, 64)          0         
    _________________________________________________________________
    conv2d_2 (Conv2D)            (None, 6, 6, 128)         73856     
    _________________________________________________________________
    max_pooling2d_2 (MaxPooling2 (None, 3, 3, 128)         0         
    _________________________________________________________________
    conv2d_3 (Conv2D)            (None, 1, 1, 128)         147584    
    _________________________________________________________________
    dropout (Dropout)            (None, 1, 1, 128)         0         
    _________________________________________________________________
    flatten (Flatten)            (None, 128)               0         
    _________________________________________________________________
    dense (Dense)                (None, 128)               16512     
    _________________________________________________________________
    dense_1 (Dense)              (None, 64)                8256      
    _________________________________________________________________
    dense_2 (Dense)              (None, 32)                2080      
    _________________________________________________________________
    dense_3 (Dense)              (None, 10)                330       
    _________________________________________________________________
    dense_4 (Dense)              (None, 1)                 11        
    =================================================================
    Total params: 268,021
    Trainable params: 268,021
    Non-trainable params: 0
    _________________________________________________________________

## Dataset

Dataset contains two classes (Malaria, Nomalaria) with a total of 5493(Class Malaria) +7258(Class Nomalaria) RGB Images. 
Each image is of 40x40 resolution.

## Sample Images

<p align="center">
  <img src="/images/sample.png" width=50% height=50% >
</p> 


## Model Performance

<p float="left">
  <img src="/images/traintestacc.png" width=50% height=50% >
</p> <p float="right">
  <img src="/images/traintestloss.png" width=50% height=50% >
</p> 


## Further Improvements

1. **Hyper-parameter Tuning** : Hyperparameters like batch_size, learning_rate, etc can be tested with different values to result into more optimal model.
2. **Data Augmentation** : It can be seen in the image samples that, Images having the parasites are like dark spot in center. So data augmentation techniques like transforming brightness, hue or contrast can be used to enhance the dark spot and helps in improving model performance.
3. **Deeper Model** : While experimenting, I found that deeper network gives more better results. So more conv layers can be added. Deeper the network, more coarse features it will extract. Ofcourse a balance should be there to not overfit the model. As complex model are more prone to overfit.
4. **Features Concatenation** : Extracted features from different pretrained network like ResNet, VGG16 or InceptionNetV3, can be concatenated to caputure more useful details in features, that possibly be missing in one set of features. Several successful reasearch has already been done in this area, for ref - [Biomedical image classification based on a feature concatenation and ensemble of deep CNNs](https://www.researchgate.net/publication/332153420_Biomedical_image_classification_based_on_a_feature_concatenation_and_ensemble_of_deep_CNNs)
5. **Use of Advanced Deep Learning Models like RetinaNet, UNet or MaskRCNN** : Advanced models like RetinaNet are build on top Feature Pyramid Network, which makes them applicable to small scale images and **"Skip-Connection/Lateral Concatenation"** in there network architecture makes it more robust towards classificatio and regression. These models proved to be successfull in obejct detection and localization.

