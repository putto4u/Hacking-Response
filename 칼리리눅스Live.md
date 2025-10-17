16GB USB 드라이브에 Kali Linux Live 부팅 환경을 만드는 방법을 순서대로 안내합니다. 이 과정은 \*\*지속성 저장 공간(Persistence)\*\*을 포함하지 않는 기본적인 Live USB 생성 방법입니다.

## 🛠️ 준비물

1.  **16GB 이상의 USB 드라이브:** (모든 데이터가 삭제되므로, 중요한 자료는 미리 백업해야 합니다.)
2.  **Kali Linux ISO 이미지 파일:** [Kali Linux 공식 웹사이트](https://www.google.com/search?q=https://www.kali.org/get-kali/%23kali-platforms)에서 다운로드합니다.
3.  **이미지 쓰기 도구 (이미저):** **Rufus** 또는 **Etcher (balenaEtcher)** 사용을 권장합니다.

-----

## 📝 Kali Linux Live USB 생성 순서

### 단계 1: ISO 파일 다운로드

1.  **Kali Linux 공식 다운로드 페이지**에서 자신의 시스템 아키텍처(대부분 **64-bit Installer** 또는 **Live** 버전)에 맞는 최신 ISO 파일을 다운로드합니다.
      * *실전 팁:* **Live** 이미지를 다운로드해야 부팅 시 설치 없이 바로 운영체제를 사용할 수 있습니다.

### 단계 2: 이미지 쓰기 도구 실행 (Rufus 사용 권장)

Windows 환경에서는 **Rufus**가 안정성과 다양한 옵션 지원 면에서 좋습니다.

1.  Rufus를 다운로드하여 실행합니다. (설치 없이 실행 가능한 포터블 버전입니다.)
2.  **USB 드라이브를 PC에 연결**합니다.

### 단계 3: Rufus 설정 및 이미지 쓰기

Rufus 화면에서 다음 설정들을 순서대로 지정합니다.

| 설정 항목 | 설정 값 | 설명 |
| :--- | :--- | :--- |
| **장치 (Device)** | 연결된 **16GB USB 드라이브** 선택 | **⚠️ 드라이브 문자를 반드시 확인하세요.** |
| **부트 선택 (Boot selection)** | **Disk or ISO image (Please select)** | 오른쪽 **'선택'** 버튼을 눌러 다운로드한 **Kali Linux ISO 파일**을 지정합니다. |
| **이미지 옵션 (Image option)** | **ISO Image** 또는 **DD Image** (ISO 모드 권장) | Rufus가 묻는 창이 뜨면 \*\*'ISO Image 모드'\*\*를 선택하세요. |
| **파티션 구성표 (Partition scheme)** | **GPT** | 최신 UEFI 시스템과의 호환성을 위해 **GPT**를 선택하는 것이 좋습니다. |
| **대상 시스템 (Target system)** | **UEFI (non CSM)** | GPT 선택 시 자동으로 선택됩니다. |
| **볼륨 레이블 (Volume label)** | 기본값 유지 (예: `KALI-LIVE`) | 필요에 따라 이름을 지정합니다. |

### 단계 4: ISO 쓰기 시작

1.  모든 설정이 완료되면, 하단의 **'시작'** 버튼을 클릭합니다.
2.  **경고 메시지** (`WARNING: ALL DATA ON DEVICE...`)가 뜨면, USB 드라이브의 데이터가 모두 삭제된다는 내용이므로 \*\*'확인'\*\*을 눌러 진행합니다.
3.  Rufus가 ISO 파일을 USB에 쓰는 작업을 완료할 때까지 기다립니다. (시간이 다소 소요될 수 있습니다.)

### 단계 5: 부팅 테스트

1.  USB 쓰기 작업이 완료되면, Rufus를 닫고 USB를 제거하지 않은 상태로 PC를 **재부팅**합니다.
2.  PC 시작 시 **BIOS/UEFI 설정 진입 키** (삼성 노트북은 보통 **F2**) 또는 **부팅 메뉴 키** (보통 **F10, F12, ESC**)를 눌러 부팅 순서를 선택합니다.
3.  부팅 옵션에서 **생성한 USB 드라이브** (일반적으로 **UEFI: [USB 제조사 이름]** 형태)를 선택합니다.
4.  Kali Linux 부팅 메뉴가 나타나면 **"Live system"** 또는 \*\*"Live (forensic mode)"\*\*를 선택하여 Kali Linux를 사용합니다.

-----

**자주 오해하거나 실수하는 부분:**

Kali Linux Live USB를 생성한 후에도 부팅이 안 된다면, 바로 전 질문에서 해결했던 것처럼 **노트북의 BIOS 설정**에서 **Secure Boot를 비활성화**하고 **OS Mode Selection을 CSM and UEFI OS로 설정**했는지 다시 한번 확인해야 합니다. 이는 USB 제작 방식의 문제가 아닌, PC의 보안 설정 문제입니다.
