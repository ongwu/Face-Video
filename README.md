## Face Video

基于单张正脸照片生成自然头部动作视频的工具。

## 资源下载
由于部分代码或模型文件体积较大，无法直接上传至 GitHub 仓库。请通过以下网盘链接下载相关资源：

链接：https://pan.quark.cn/s/2db9b42d23b6

## 项目背景
本项目旨在通过单张人脸照片自动生成具有自然感的头部动画视频，包括呼吸微动、转头和眨眼等动作，适用于数字人、虚拟形象等场景。

## 实现步骤
1. **环境准备**: 使用 `install.bat` 自动化创建虚拟环境并安装 CUDA 加速的 PyTorch。
2. **源码与模型**: 自动克隆 LivePortrait 源码并从镜像站下载预训练权重。
3. **动作编排**: 通过 `faceanim` 模块生成逐帧的姿态控制信号（Pitch, Yaw, Roll, Eye Ratio）。
4. **渲染生成**: 调用底层模型执行神经渲染，将静态图转化为动态视频。

## 核心原理
- **LivePortrait**: 核心算法基于快手开源的 LivePortrait，利用外观特征提取与隐式关键点预测。
- **动作控制**: 
  - **微动**: 结合正弦波与随机游走模拟不自主的头部晃动。
  - **转头**: 通过 Smoothstep 缓动函数控制 Yaw 轴的角度偏移。
  - **眨眼**: 模拟真实的眼睑闭合曲线。
- **渲染**: 基于隐式关键点的变形与生成器，将目标姿态实时渲染到源图像。

## 使用说明

### 环境要求
- Windows 10/11
- NVIDIA GPU (建议)
- Python 3.9/3.10
- Git

### 快速启动
1. **安装环境**: 双击运行 `install.bat`。
2. **生成视频**: 双击运行 `run.bat`。
   - 默认输入: `assets/input/face.jpg`
   - 输出路径: `assets/output/`

### 进阶用法
在命令行中指定参数：
```bash
run.bat --image [图片路径] --action [all|frontal|left|right|blink] --duration [时长]
```

## 目录结构
- `install.bat`: 一键安装脚本
- `run.bat`: 一键启动脚本
- `generate.py`: 主程序入口
- `faceanim/`: 核心封装模块
- `assets/`: 输入输出资源

---

> 开发者：ongwu
> 
> 电子邮箱：ongwu007@gmail.com
> 
> GitHub： [https://github.com/ongwu](https://https://github.com/ongwu)
> 
> 官方网站：[https://www.262944.xyz](https://https://www.262944.xyz)
