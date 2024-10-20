# Image Captioning Project

This project implements an image captioning model using deep learning techniques. It combines the InceptionV3 model for image feature extraction with an LSTM-based model for generating captions from images.

## Dataset Used

The dataset used for this project is **Flickr8k**, which contains 8,000 images with five different captions each. The dataset is split into training, validation, and test sets.

You can download the dataset from [Flickr8k Dataset](https://github.com/jbrownlee/Datasets/releases/download/Flickr8k/Flickr8k_Dataset.zip) and the captions from [Flickr8k Text](https://github.com/jbrownlee/Datasets/releases/download/Flickr8k/Flickr8k_text.zip).









## How the Code Works

### Step 1: Preprocessing Images
The InceptionV3 model is used to extract features from the images. The image features are preprocessed using the `preprocess_input` function from `tensorflow.keras.applications.inception_v3`. Images are resized and converted into arrays before passing them to the model for feature extraction.

### Step 2: Preprocessing Text
The captions are tokenized using Keras' `Tokenizer`. Each word is mapped to a unique integer, and sequences are padded to a consistent length. The captions are cleaned, tokenized, and padded to create uniform sequences.

### Step 3: Model Architecture
The model architecture consists of:
- **Image Feature Extractor:** A pretrained InceptionV3 model, where the top layer is removed to extract image features.
- **Text Processing Layer:** An embedding layer followed by an LSTM network that processes the text input.
- **Combining Image and Text Features:** The image and text features are concatenated and passed through dense layers to predict the next word in the caption.

### Step 4: Training the Model
The model is trained using the training dataset. The image features and the corresponding tokenized captions are passed to the model. The Adam optimizer is used to minimize the categorical crossentropy loss function. The model learns to predict the next word in the sequence for each caption.

### Step 5: Caption Generation
Once the model is trained, captions can be generated for new images. The image is passed through the feature extractor (InceptionV3), and the trained model predicts the caption one word at a time until the full sentence is generated.


## Directory Structure

```plaintext
.
├── Flickr8k_Dataset/
│   ├── Flickr_8k.trainImages.txt
│   ├── Flickr_8k.devImages.txt
│   ├── Flickr_8k.testImages.txt
│   └── Images/  # All images in this folder
└── captions.txt  # All captions in a text file
