# Deep Learning Architectures for Image Colorization

## Project Overview

We conducted a comprehensive comparative analysis of deep learning architectures for automatic image colorization. The project explores the evolution of colorization techniques, moving from standard regression-based approaches (Encoder-Decoder) to advanced generative models (GANs). The goal was to benchmark how different architectures handle the prediction of chromaticity ($a, b$) channels given a grayscale ($L$) input.

## Architectures Implemented

We implemented and trained the following 6 architectures to compare performance:

1.  **Basic Encoder-Decoder (Regression):** A standard vanilla autoencoder trained to minimize Mean Squared Error (MSE).
2.  **Encoder-Decoder (AB Regression):** Optimized specifically to predict the $a$ and $b$ channels of the **CIE L\*a\*b\*** color space while preserving the $L$ (Lightness) channel.
3.  **CNN Model:** A deep Convolutional Neural Network without the bottleneck structure, focusing on feature extraction.
4.  **U-Net:** Implementing skip connections to preserve high-frequency spatial details lost during downsampling.
5.  **DCGAN (Deep Convolutional GAN):** A generative approach where the Generator predicts colors and the Discriminator differentiates between real and colorized images.
6.  **ChromaGAN + U-Net:** A hybrid approach leveraging the semantic understanding of ChromaGAN combined with the structural details of U-Net.

## 📊 Comparative Analysis & Results

We evaluated the models using **PSNR** (Peak Signal-to-Noise Ratio) and **SSIM** (Structural Similarity Index Measure).

| Model Architecture | PSNR (dB) | SSIM | Training Time (hrs) | Key Observation |
|:---|:---:|:---:|:---:|:---|
| Basic Encoder-Decoder | 18.2 | 0.65 | 2.5 | Resulted in sepia/desaturated tones. |
| AB Regression | 20.1 | 0.71 | 3.0 | Better color variance, but edges were blurry. |
| CNN Model | 21.5 | 0.74 | 4.0 | Sharp features, but inconsistent color patches. |
| U-Net | 24.8 | 0.82 | 5.5 | Good structural consistency. |
| DCGAN | 22.1 | 0.76 | 8.0 | Plausible colors, but suffered from mode collapse. |
| ChromaGAN + U-Net | 25.2 | 0.85 | 10.0 | State-of-the-art visual quality. |

> *Note: This is a placeholder, I will update it with real values in some days.*

## 🔧 Mathematical Context

For the regression-based models, we utilized the **CIE L\*a\*b\*** color space. The grayscale input serves as the $L$ channel (Lightness), and the model aims to approximate the mapping function $F$ such that:

$$(a, b) = F(L)$$

The loss function for the generative models (DCGAN/ChromaGAN) combined pixel-wise loss with adversarial loss:

$$\mathcal{L}_{total} = \lambda_{1}\mathcal{L}_{L1} + \lambda_{2}\mathcal{L}_{GAN}$$

> *Note: This is an ongoing project, I will add the code and results for the other architectures in some days.*
