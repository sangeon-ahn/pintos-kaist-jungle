# Pintos (KAIST / Krafton Jungle)

[한국어 (Korean)](#korean) | [English](#english)

<a name="korean"></a>

## 한국어 (Korean)

이 프로젝트는 KAIST 및 크래프톤 정글(Krafton Jungle) 과정의 운영체제 및 실습(CS330)에서 사용되는 **Pintos** 운영체제 프레임워크입니다. 운영체제 설계 및 구현의 핵심 개념을 학습하기 위해 설계된 교육용 x86_64 운영체제입니다.

### 📚 문서 (Documentation)

공식 매뉴얼은 이 프로젝트의 주요 참고 자료입니다:
👉 **[KAIST Pintos 매뉴얼](https://casys-kaist.github.io/pintos-kaist/)**

### 📂 프로젝트 구조

저장소 구조는 다음과 같습니다:

- **`threads/`**: 기본 커널 소스 코드 (스레드 스케줄러, 동기화 도구, 인터럽트 처리 등). (Project 1)
- **`userprog/`**: 사용자 프로그램 로드 및 실행 지원 (인자 전달, 시스템 콜 등). (Project 2)
- **`vm/`**: 가상 메모리 구현 (페이지 테이블, 스왑, 스택 확장 등). (Project 3)
- **`filesys/`**: 파일 시스템 구현. (Project 4)
- **`devices/`**: I/O 장치 인터페이스 소스 코드 (키보드, 타이머, 디스크, VGA 등).
- **`lib/`**: 표준 C 라이브러리의 일부 구현 (커널 및 사용자용).
- **`tests/`**: 채점을 위한 종합 테스트 모음.
- **`utils/`**: Pintos 실행을 위한 헬퍼 스크립트 (`pintos` 래퍼 스크립트 포함).
- **`include/`**: 커널 전반에서 공유되는 헤더 파일.

### 🚀 시작하기

#### 필수 요구 사항

Linux 기반 환경 (또는 Windows의 WSL)과 다음 도구들이 필요합니다:
- GCC (x86_64 설정)
- GDB
- QEMU (x86_64 에뮬레이터)
- Make
- Perl

#### 환경 설정

`pintos` 명령어를 어디서든 사용할 수 있도록 `utils` 디렉토리를 `PATH`에 추가합니다.

```bash
export PATH=$PATH:$(pwd)/utils
```

#### 빌드하기

Pintos는 각 프로젝트 단계별로 별도로 빌드됩니다. 프로젝트 하위 디렉토리(예: `threads`, `userprog`, `vm`, `filesys`)로 이동하여 `make`를 실행하세요.

**예시: Project 1 (Threads) 빌드**

```bash
cd threads
make
```

`build/` 디렉토리가 생성되며, 컴파일된 커널(`kernel.o`)과 디스크 로더(`loader.o`)가 포함됩니다.

### 🏃 Pintos 실행하기

`pintos` 유틸리티를 사용하여 QEMU에서 운영체제를 실행합니다.

**예시: 특정 테스트 케이스 실행**
```bash
# threads 디렉토리에서
pintos -- -q run alarm-multiple
```

**예시: GDB를 사용한 디버깅**
```bash
pintos --gdb -- -q run alarm-multiple
```

### 🧪 테스트

각 프로젝트에는 고유한 테스트 세트가 있습니다. `make check`를 사용하여 현재 프로젝트의 모든 테스트를 실행할 수 있습니다.

```bash
cd threads
make check
```

`build/tests/` 디렉토리에 컴파일된 특정 테스트를 실행하려면:

```bash
cd build
make tests/threads/alarm-multiple.result
```

### 🧹 정리하기 (Clean)

빌드 산출물을 삭제하고 디렉토리를 정리하려면:

```bash
make clean
```

---

<a name="english"></a>

## English

This is the **Pintos** operating system framework, specifically the version used for Operating Systems and Lab (CS330) at KAIST and the Krafton Jungle program. It is an educational x86_64 operating system designed to introduce key concepts in OS design and implementation.

### 📚 Documentation

The official manual is the primary reference for this project:
👉 **[KAIST Pintos Manual](https://casys-kaist.github.io/pintos-kaist/)**

### 📂 Project Structure

The repository is organized as follows:

- **`threads/`**: Source code for the base kernel, which includes the thread scheduler, synchronization primitives, and interrupt handling. (Project 1)
- **`userprog/`**: Support for loading and running user programs, including argument passing and system calls. (Project 2)
- **`vm/`**: Virtual memory implementation, including page tables, swap, and stack growth. (Project 3)
- **`filesys/`**: File system implementation. (Project 4)
- **`devices/`**: Source code for I/O device interfacing (keyboard, timer, disk, VGA, etc.).
- **`lib/`**: Implementation of a subset of the standard C library (kernel and user).
- **`tests/`**: Comprehensive test suite for grading.
- **`utils/`**: Helper scripts for running Pintos, including the `pintos` wrapper script.
- **`include/`**: Header files shared across the kernel.

### 🚀 Getting Started

#### Prerequisites

You need a Linux-based environment (or WSL on Windows) with the following tools installed:
- GCC (configured for x86_64)
- GDB
- QEMU (x86_64 emulator)
- Make
- Perl

#### Setting up Environment

Add the `utils` directory to your `PATH` so you can use the `pintos` command anywhere.

```bash
export PATH=$PATH:$(pwd)/utils
```

#### Building

Pintos is built separately for each project phase. Navigate to the project subdirectory (e.g., `threads`, `userprog`, `vm`, `filesys`) and run `make`.

**Example: Building Project 1 (Threads)**

```bash
cd threads
make
```

This creates a `build/` directory containing the compiled kernel (`kernel.o`) and the disk loader (`loader.o`).

### 🏃 Running Pintos

Use the `pintos` utility to run the operating system in QEMU.

**Example: Running a specific test case**
```bash
# In the threads directory
pintos -- -q run alarm-multiple
```

**Example: Debugging with GDB**
```bash
pintos --gdb -- -q run alarm-multiple
```

### 🧪 Testing

Each project has its own set of tests. You can run all tests for the current project using `make check`.

```bash
cd threads
make check
```

To run a specific test, compiled in the `build/tests/` directory:

```bash
cd build
make tests/threads/alarm-multiple.result
```

### 🧹 Cleaning

To remove build artifacts and clean the directory:

```bash
make clean
```
