# 실전 추천시스템 알고리즘 이해와 구현

2025 / 06 /16 ~ 06 / 18

## 강사

멀티캠퍼스 강선구(sunku0316.kang@multicampus.com, sun9sun9@gmail.com)

## 기본 환경 구성

Windows 10 / WSL Ubuntu(24.04) / Python 3.12.9

Window에서 가상 환경으로 Ubuntu를 구동 시켜서 진행합니다. 

순수한 Linux 환경이 사용이 어려우실 수 있어 WSL로 구성했습니다. 

동일 장비에서 테스트해본 결과 순수 Linux 환경과 WSL의 성능 차이는 약 5배 정도 차이납니다. 

여러 가지 실험을 이어 나가시고자 한다면, 순수 Linux 장비 구성을 강력히 권합니다.

순수 Linux는 Ubuntu를 사용한다면, 아래 방법과 크게 차이나지 않습니다.

## NVIDIA 드라이브 업데이트

- NVIDIA 장비 확인
시스템 > 정보 > 고급 시스템 설정

- NVIDIA 드라이버 업데이트


강의장 PC 기준

https://www.nvidia.com/ko-kr/drivers/details/241094/

설치 파일 다운로드 

실행 > NVIDIA 그래픽 드라이버 > 빠른 설치

## WSL 설치

커맨드창을 구동 시킵니다.

```cmd
wsl --install --distribution Ubuntu
```

.wslconfig 파일을 /user/student 폴더에 만듭니다.
```
# Settings apply across all Linux distros running on WSL 2
[wsl2]

# Limits VM memory to use no more than 24 GB, this can be set as whole numbers using GB or MB
memory=24GB 

# Sets the VM to use 6 virtual processors
processors=6

# Sets amount of swap storage space to 24GB, default is 25% of available RAM
swap=24GB
```

WSL 구동

```cmd
wsl -d Ubuntu
```
user account: rcmd/rcmd2025

```bash
sudo apt update
sudo apt full-upgrade -y
```

CPU와 메모리 현황을 봅니다.
```
lscpu
free -h
```



## 실습환경 구축

### Docker 설치

[Docker](https://www.docker.com/get-started/)에서 설치 프로그램을 다운로드 받습니다.

### Docker 이미지 다운로드

[오라클 이미지](https://drive.google.com/file/d/1gjBAFlSTNfYWN4q5g-2pJ5LaTSkUNaT7/view?usp=drive_link)

[Qdrant 이미지](https://drive.google.com/file/d/1nnvgbnBvZtrAubOTuAajQllvcSWccb5h/view?usp=drive_link)

[실습환경 이미지](https://drive.google.com/file/d/1wZzDF3B2EYj5BpXIqBfE37UvZiILNw21/view?usp=drive_link)

### Docker 이미지 탑재

커멘드 창을 열고 docker 이미지가 있는 경로로 이동합니다.

1. Oracle Image 탑재

```
docker load -i oracle-rcmd.tar
```

2. Qdrant Image 탑재

```
docker load -i qdrant_rcmd.tar
```

3. 실습 환경 탑재

```
docker load -i multi_rcmd.tar
```
