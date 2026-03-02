# LiDAR-Camera Semantic Segmentation Fusion

A ROS-based pipeline that fuses LiDAR point cloud data with camera-based semantic segmentation using DeepLabV3+ for real-time scene understanding.

![Output](https://github.com/thakkar-nit/Lidar_SemSeg_Fusion/blob/master/final_output.gif)

## Overview

This project combines 2D semantic segmentation from a camera feed with 3D LiDAR point clouds to produce semantically labeled 3D scene representations. The system uses a pretrained DeepLabV3+ model with a MobileNet backbone (trained on Cityscapes) for pixel-wise semantic segmentation, then projects the labels onto the LiDAR point cloud using extrinsic calibration between the RealSense camera and LiDAR sensor.

## Pipeline

```
Camera Feed ──► DeepLabV3+ (MobileNet) ──► Semantic Labels
                                                │
LiDAR Point Cloud ──────────────────────────────┤
                                                │
Camera-LiDAR Calibration ──────────────────► Fused 3D Semantic Map
```

## Features

- Real-time semantic segmentation using DeepLabV3+ with MobileNet backbone
- RealSense camera intrinsic calibration pipeline
- LiDAR-camera extrinsic calibration and projection
- ROS node architecture for modular sensor fusion
- Cityscapes-trained model for urban scene understanding

## Tech Stack

`Python` · `PyTorch` · `ROS` · `OpenCV` · `PCL` · `DeepLabV3+` · `RealSense`

## Prerequisites

- ROS (with catkin workspace)
- Python 3 with PyTorch
- RealSense SDK (for camera calibration)
- LiDAR driver (compatible with ROS)

## Getting Started

```bash
git clone https://github.com/pathal-r/Lidar-camera-Segmentation-Fusion.git
cd Lidar-camera-Segmentation-Fusion
pip install -r requirements.txt
```

### Run

```bash
cd sem_seg/src/semantic_segment
bash run.sh
```

## Project Structure

```
Lidar-camera-Segmentation-Fusion/
├── src/semantic_segment/
│   ├── network/          # DeepLabV3+ model architecture
│   ├── datasets/         # Cityscapes and VOC dataset utilities
│   ├── utils/            # Transforms, loss, visualization
│   ├── publisher.py      # ROS publisher node
│   └── myscript.py       # Main inference script
├── sem_seg/              # ROS catkin workspace
├── Relasense_Calibration/# Camera calibration scripts and images
└── requirements.txt
```
