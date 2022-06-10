# CSE-455-Final-Project
By Rohit Ramesh and Akhilesh Varanasi


# What are we trying to solve?
We are trying to solve the I Was Busy Thinkin' 'Bout Birds Kaggle Competition. We are trying to achieve a high classification accuracy in classifying different bird species.

Link to Kaggle Competition: https://www.kaggle.com/competitions/birds22sp/overview

Our Overall Rank on Kaggle Leaderboard: 5

Model Accuracy: 81.8%
# Strategy and Techniques used
Our strategy varied throughout the project. At first, we were trying to use a leaky ReLU-Sigmoid model with CrossEntropy Loss. However, this turned out to be taking too much time to run for our google colab. We switched to a simple linear model with no activation functions and passed that into variations of resnet18, resnet34, resnet50, and resnet152. We also varied the size of the images between values of 128,160,256,384 and varied the batch size for ease of training. We found that image size and resnet complexity had a significant effect on the accuracy of our model. For example, a size of 160 over 128 raised our accuracy by 3% and resnet34 over resnet18 improved our model by almost 10%. We found that resnet50 and resnet152 were too large for our colab space so we decided on resnet34, image size of 384x384 and a batch size of 128, with 25 epochs. We did not attempt hyperparameter training as that would have required more resources than available to us so we stuck with a reasonable default learning rate of 0.01, momentum of 0.9, and a weight decay of 0.0005. We also used Stochastic Gradient Descent for our optimizer.
# Dataset
We got our dataset from the data provided by the Kaggle Competition. This included the test/train images and the text file containing the names of the birds. There are 10,000 images in the test directory and there are approximately 38,000 images in the train directory. The text file contains 555 different bird species names.
# Graphs
The following graph represents the decline in loss over time as the model was training

![Loss vs Iters](https://user-images.githubusercontent.com/60229228/172990003-e9471980-9812-4d5d-b42b-27b7235d0f4d.png)

# Inspiration from Previous Work

We drew inspiration from the Transfer Learning to Pytorch Tutorials provided on the course website to get a better understanding of working with PyTorch in Google Colab. For example, after reading about how the dataset definition worked, we decided to do something similar in the process of connecting our dataset to PyTorch. Our train was fairly straightforward and based on methods we've created for classes like CSE 446. We processed data in batches, took forward and backward steps while calculating loss, and updated model architecture every epoch.
