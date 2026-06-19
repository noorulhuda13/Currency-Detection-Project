Currency Recognition System

A MATLAB-based currency recognition system that automatically identifies world currency banknotes from digital images using multi-stage image processing and nearest-neighbor classification.

📋 Overview

This system processes digital images of banknotes and identifies the currency type using a multi-feature extraction approach combining color, texture, and edge information. It features a fully interactive GUI with real-time visualization of all processing stages.

Key Features

7-step image processing pipeline with real-time visualization
Multi-feature extraction (Color, Edge, GLCM Texture)
78-dimensional feature vector
1-Nearest Neighbor classification with Euclidean distance
MSE and PSNR quality metrics
Database of 17 world currencies with national flags
Interactive MATLAB GUI
🚀 Getting Started

Prerequisites

MATLAB R2018a or later
Image Processing Toolbox
Statistics and Machine Learning Toolbox
Installation


📁 Project Structure

text
Currency-Recognition-System/
├── MY.m                 # Main controller with callbacks
├── MY_GUI.m             # GUI layout definition
├── color_luv.m          # Color feature extraction (LUV space)
├── edgehist.m           # Edge orientation histogram
├── totalfeature.m       # Feature combiner (78-D vector)
├── rebuild_db.m         # Database builder
├── projectdb.mat        # Pre-built feature database
├── Currency Dataset/    # Training images
│   ├── australiandollar.jpg
│   ├── dollar.jpg
│   ├── indianrupee.jpg
│   └── ... (17 currencies)
├── Flags/               # National flag images
│   ├── india.png
│   ├── usa.png
│   └── ... (17 flags)
└── README.md
🔧 System Architecture

7-Step Image Processing Pipeline

Step	Stage	Algorithm	Output
1	Resize	imresize(img, [128 128])	128×128 RGB
2	Denoise	medfilt2() per channel	Filtered RGB
3	Noise Map	imabsdiff() ×25, MSE, PSNR	Noise visualization
4	Enhancement	rgb2hsv → histeq(V) → hsv2rgb	Enhanced RGB
5	Edge Detection	edge(gray, 'sobel')	Binary edge map
6	Segmentation	imbinarize() - Otsu's method	Binary mask
7	Morphological Clean	imopen(strel('disk',1))	Cleaned binary
