### Convert PyTorch models to ONNX and then to TensorRT
[![Build Status](https://app.travis-ci.com/ucLh/torch2onnx2trt.svg?branch=master)](https://app.travis-ci.com/ucLh/torch2onnx2trt)
#### Requirements
1) PyTorch (for int8 mode version 1.9 or higher is required)
2) TensorRT (tested with 8.0)
3) The rest of the requirements are listed in `requirements.txt` and can
 be installed automatically via `pip` installation
 
Alternatively, you can skip installation of the requirements and use 
[this](https://hub.docker.com/r/uclh/tensorrt_pytorch) docker container 
 
#### Installation
There is `setup.py` file in the repo, so the installation is pretty 
straightforward
```
git clone https://github.com/ucLh/torch2onnx2trt.git
cd torch2onnx2trt
pip3 install -e ./
```

#### Usage
```python
from torch2onnx2trt import convert_torch2onnx, convert_onnx2trt
# Load your pretrained model
pretrained_model = ...
# You need to pass your model with loaded weights, an output path for onnx model
# and desired input shape to convert_torch2onnx function
convert_torch2onnx(pretrained_model, 'effnetb0_unet_gray_2grass_iou55.onnx', (1, 3, 640, 1280))
# convert_onnx2trt expects a path to onnx model and an output path for resulting
# TensorRT .bin model
convert_onnx2trt('../effnetb0_unet_gray_2grass_iou55.onnx', '../effnetb0_unet_gray_2grass_iou55.bin')
```
