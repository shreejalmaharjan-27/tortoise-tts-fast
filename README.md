# 🐢 This is a fork of the tortoise-tts-fast fork 
This fork is exactly the same as the original tortoise-tts-fast but adds deepspeed for even faster inference speed

The original tortoise repo has many of these changes merged in but it does not allow you to import finetuned tortoise models

---

# Speeding up TorToiSe inference 5x

This is a working project to drastically boost the performance of TorToiSe, without modifying the base models. **Expect speedups of _5~10x_**

This repo adds the following config options for TorToiSe for faster inference:

- [x] New September 2023 - Deepspeed
- [x] (`--kv_cache`) enabling of [KV cache](https://kipp.ly/blog/transformer-inference-arithmetic/#kv-cache) for MUCH faster GPT sampling
- [x] (`--half`) half precision inference where possible
- [x] (`--sampler dpm++2m`) [DPM-Solver](https://github.com/LuChengTHU/dpm-solver) samplers for better diffusion
- [x] (disable with `--low_vram`) option to toggle cpu offloading, for high vram users

All changes in this fork are licensed under the **AGPL**. For avoidance beyond all doubt, the [following statement](https://en.wikipedia.org/wiki/Apache_License#Licensing_conditions) is added as a comment to all changed code files:

> `AGPL: a notification must be added stating that changes have been made to that file. `

## Installation

### pure python install

The installation process is identical to the original tortoise-tts repo. Unfortunately, deepspeed is not supported on Windows (which is ironic because the repo is operated by Microsoft). So to install deepspeed I recommend using WSL. Luckily, WSL is not too painful to setup and integrates pretty well with VS code. 

```shell
conda create --name tortoise python=3.9 numba inflect
conda activate tortoise
conda install pytorch==2.0.0 torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia
conda install transformers=4.29.2
pip install -r requirements.txt 
pip3 install git+https://github.com/152334H/BigVGAN.git
pip install deepspeed=0.10.2 # linux/WSL only
```

If you are on windows, you will also need to install pysoundfile: `conda install -c conda-forge pysoundfile`

### For more information please reference the original tortoise-tts-fast README or original tortoise repo README
