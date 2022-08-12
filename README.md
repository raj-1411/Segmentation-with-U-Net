# Segmentation-with-U-Net
Python-based project performing binary segmentation on `PH2` dataset : https://www.dropbox.com/s/k88qukc20ljnbuo/PH2Dataset.rar?file_subpath=%2FPH2Dataset
This project generated binary masks from dermatological samples fed into the system which are ultimately classified into three categorical divisions. 

## Project Description
The motivation to achieve `enhanced` accuracy on predictions made by different Deep Learning techniques - Segmentation and Classification. Sometimes, CNNs when fed with three channel images fail to learn structural information necessary to classify them. Annotated training data with boundaries clearly defined enables efficient detection and learning. Segmentation network used in medical imaging generates binary masks which when fed to a classification network performs much better. For this project, popular `PH2` dataset was employed to verify segmentation, followed by classificaton between common_nevus, atypical_nevus and melanoma types of dermatology samples of affected tissue. For feature extraction, `Efficient-net-b4-widese` is used with their `pre-final` layer modified for the need of the objective. As the network is trained and evaluated on annotated masks, model weights are saved having the best performance w.r.t. the loss function employed. Consequently, the test dataset is fed to the system to generate masks followed by classifier network classfiying them.

## Dataset description
The increasing incidence of melanoma has recently promoted the development of computer-aided diagnosis systems for the classification of dermoscopic images. The PH² dataset has been developed for research and benchmarking purposes, in order to facilitate comparative studies on both segmentation and classification algorithms of dermoscopic images. PH² is a dermoscopic image database acquired at the Dermatology Service of Hospital Pedro Hispano, Matosinhos, Portugal.  
The dataset is available at:    
[https://web.inf.ufpr.br/vri/databases/breast-cancer-histopathological-database-breakhis/](https://www.fc.up.pt/addi/ph2%20database.html)

## Classes of Division
In this project, the histopathological image samples of human breast tissue have been classified into two categories  
- `Common Nevus`  
- `Atypical Nevus`
- `Melanoma`  

## Convolution Neural Network models used
Network Architectures Used:
-	Segmentation: `U-Net`  
-	Classifier: `EfficientNet-b4-widese`  

## Classifiers used
Three types of classifiers are employed for fitness evaluation
-	`Support Vector Machines (kernel<--rbf)`  
-	`K Nearest Neighbours (neighbours<--2)`  
-	`Multi-layer Perceptron` 

## Overall Network Visualization:
-     Roadmap
     !![7ff5fc1c9d7e7b76a10af4ef0b6cb36f-1](https://user-images.githubusercontent.com/89198752/184345453-bb4a3d4a-c844-406b-b206-7e90fe061028.jpg)

## Classification Accuracy Plots Over Generations
MLP classifer gives following plot of accuracy vs generations:
Epoch-`200`
     ![image](https://user-images.githubusercontent.com/89198752/154793637-f36ce72c-6483-4755-9d04-622327210d48.png)

## Dependencies
Since the entire project is based on `Python` programming language, it is necessary to have Python installed in the system. It is recommended to use Python with version `>=3.9`.
The Python packages which are in use in this project are  `matplotlib`, `numpy`, `pandas`,`scikit-learn`, `torch` and `torchvision`. All these dependencies can be installed just by the following command line argument
- `pip install requirements.txt`

## Code implementation
 ### Data paths :
      Current directory ---->   data
                                  |
                                  |
                                  |               
                                  ------------------>  train
                                  |                      |
                                  |             -------------------------
                                  |             |        |              |
                                  |             V        V              V
                                  |          class 1   class 2 ..... class n
                                  |
                                  |
                                  |              
                                  ------------------>   val
                                                         |
                                                -------------------------
                                                |        |              |
                                                V        V              V
                                             class 1   class 2 ..... class n
                                              
                               
- Where the folders `train` and `val` contain the folders for different classes of histopathological images of respective type of breast tissue tumor in `.jpg`/`.png` format.

 ### Training and Evaluation :
      usage: main.py [-h] [-data DATA_PATH] [-classes NUM_CLASSES] [-ext EXT_TYPE] [-classif CLASSIF_TYPE]

      Application of Genetic Algorithm

      optional arguments:
        -h, --help            show this help message and exit
        -data DATA_PATH, --data_path DATA_PATH
                              Path to data
        -classes NUM_CLASSES, --num_classes NUM_CLASSES
                              Number of data classes
        -ext EXT_TYPE, --ext_type EXT_TYPE
                              Choice of extractor
        -classif CLASSIF_TYPE, --classif_type CLASSIF_TYPE
                              Choice of classifier for GA
        
  ### Run the following for training and validation :
  
      python main.py -data data -classes n -ext resnet -classif MLP
      
  ### Specific tokens :

      GoogLeNet: 'googlenet'
      VGG-19: 'vgg'
      ResNet-18: 'resnet'
      SVM: 'SVM'
      MLP: 'MLP'
      KNN: 'KNN'          
