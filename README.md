### 🚀 Machine Learning Project Study
> RTX 3060 로컬 환경에서 진행하는 머신러닝 학습 저장소입니다.

### 📌 Project Overview
이 프로젝트는 머신러닝의 기초 알고리즘(로지스틱 회귀, 결정 트리 등)을 학습하고, 
실제 데이터셋에 적용하여 모델을 구축하는 것을 목표로 합니다.

### 🛠 Environment
- **OS**: Windows 11 (WSL2 Ubuntu 24.04 LTS)
- **Language**: Python 3.10
- **IDE**: Conda + VS Code
- **Main Libraries**: Scikit-learn, Pandas, PyTorch
- **Hardware**: NVIDIA GeForce RTX 3060 (GPU 가속 활용)

### 📁 Project 생성
1. **NVIDIA 공식 홈페이지에서 최신 드라이버(Game Ready 또는 Studio)를 설치**
    https://www.nvidia.com/en-us/drivers/

2. **CUDA Toolkit 설치**
    https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local

3. **WSL2 및 Ubuntu 설치**
    ```powershell
    $ wsl --install
    ```

4. **VS Code Extendsion 설치 (NVIDIA 쓰려면 Admin 권한으로 항상 VSC 키자)**
    - WSL
    - Python
    - Jupyter

5. **Miniconda(가상환경) 설치**
    ```bash
    $ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
    $ bash Miniconda3-latest-Linux-x86_64.sh

    # 약관 동의
    $ conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/main
    $ conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/r
    ```

    ```bash
    $ mkdir ml_study
    $ cd ml_study
    $ conda create -n ml_study python=3.10
    $ conda activate ml_study
    $ touch .gitignore
    ```

6. **ML 라이브러리 및 Jupyter 설치**
    ```bash
    $ pip install numpy pandas scikit-learn matplotlib jupyter
    $ pip install torch
    ```

7. **동작 확인**
    ```python
    # test.ipynb
    import torch

    # 1. GPU 연결 확인
    print(f"GPU 사용 가능 여부: {torch.cuda.is_available()}")

    # 2. 내 그래픽카드 이름 확인
    if torch.cuda.is_available():
        print(f"사용 중인 장치: {torch.cuda.get_device_name(0)}")

    # 3. 간단한 행렬 연산으로 테스트
    x = torch.randn(1000, 1000).to("cuda")
    y = torch.randn(1000, 1000).to("cuda")
    z = torch.matmul(x, y)
    print("GPU 행렬 연산 완료!")
    ```
    ```bash
    $ jupyter notebook
    ```
    ```bash
    GPU 사용 가능 여부: True
    사용 중인 장치: NVIDIA GeForce RTX 3060
    GPU 행렬 연산 완료!
    ```