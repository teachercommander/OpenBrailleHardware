# OpenBraille

## 📘 프로젝트 개요
OpenBraille은 시각장애인을 위한 IoT 기반 점자 통신 시스템으로, 근접 인식 촉각 인터페이스를 통해 지원합니다. 이 프로젝트는 Bluetooth Low Energy(BLE) 기술과 초음파 센서를 결합하여 플랫폼을 구축합니다.

## 🏗️ 시스템 아키텍처

### 🔧 하드웨어 구성요소
- **ESP32 마이크로컨트롤러**: BLE 통신을 위한 주요 처리 장치
- **WeMos D1 Mini**: 센서 통합을 위한 IoT 개발 보드

### 📡 통신 스택
- **BLE (Bluetooth Low Energy)**: RSSI를 이용한 장치 발견 및 근접 감지
- **WiFi 연결**: IoT 도어 제어 및 원격 모니터링
- **시리얼 통신**: 디버그 및 모니터링 인터페이스

## 🛠 주요 기능

### 1. **근접 감지 시스템**
- ESP32 기반 BLE 애드버타이저 및 스캐너 쌍
- 실시간 RSSI 측정을 통한 거리 추정
- 자동 장치 발견 및 추적

### 2. **공간 인식**
- 초음파 거리 측정
- 환경 장애물 감지
- 실시간 거리 피드백

### 3. **IoT 통합**
- 스마트 도어 제어 시스템
- 원격 센서 모니터링
- 확장 가능한 IoT 장치 네트워크

## 📁 프로젝트 구조

```
OpenBraille/
├── 2_firmware/
│   └── ble/
│       ├── esp32_ble_rssi_Advertiser/    # BLE 브로드캐스팅 장치
│       └── esp32_ble_rssi_Scanner/       # BLE 스캔 및 RSSI 측정
└── 4_Example_code/
    └── IOT_Door/
        ├── Ex_server/                    # WiFi 서버 구현
        └── Ex_sonic_distance/            # 초음파 센서 통합
```

## 🔬 기술적 구현

### BLE 통신
- **애드버타이저**: 장치 발견을 위한 "ESP32_A" 식별자 브로드캐스트
- **스캐너**: 대상 장치 감지 및 RSSI 값을 이용한 근접도 계산
- **거리 알고리즘**: `거리 = 10^((txPower - RSSI) / (10 * n))` (n=2.0)

### 센서 통합
- **초음파 범위**: TRIG/ECHO 핀 구성의 HC-SR04 센서
- **거리 계산**: `거리 = duration * 17 / 1000` (센티미터 단위)
- **실시간 처리**: 1초 간격 측정

## 🚀 시작하기

### 필수 요구사항
- PlatformIO IDE 또는 Arduino IDE
- ESP32 개발 보드
- HC-SR04 초음파 센서
- 프로그래밍용 USB 케이블

### 설치 방법
```bash
git clone https://github.com/username/OpenBraille.git
cd OpenBraille
```

### 펌웨어 빌드
```bash
# BLE 애드버타이저용
cd 2_firmware/ble/esp32_ble_rssi_Advertiser
platformio run --target upload

# BLE 스캐너용
cd ../esp32_ble_rssi_Scanner
platformio run --target upload
```

## 🗓️ 개발 기록
- **2025-05-09**: ChatBraille에서 OpenBraille로 프로젝트명 변경
- **2025-05-07**: 초기 GitHub 저장소 설정

## 🎯 향후 개발 계획
- 점자 인코딩/디코딩 알고리즘
- 다중 장치 통신 프로토콜
- 모바일 앱 통합
- 향상된 공간 매핑 기능

## 👥 개발팀
```
김남주, 김혜경, 민성조, 박석희, 박지훈, 박하진, 윤승진, 윤창훈, 장태이, 황도윤
```

## 추가 레포지토리
개발자들의 관리용으로 쓰기 위해 프론트엔드를 개발 중
- 우리가 갖고 있는 맥 주소
- 현재 기기를 사용하고 있는지 여부

## 📄 라이선스
이 프로젝트는 보조 기술 연구 및 교육 목적으로 개발되었습니다.
