<p align="center">
  <img src="https://raw.githubusercontent.com/ops-jaeha/cutmaru-releases/main/assets/cutmaru-symbol.png" width="112" height="112" alt="cutmaru 로고">
</p>

<h1 align="center">cutmaru</h1>

<p align="center"><strong>7시간짜리 SOOP 방송에서 편집에 쓸 장면을 찾는 Windows 앱</strong></p>

<p align="center">
  <a href="#다운로드">다운로드</a> ·
  <a href="#빠른-시작">빠른 시작</a> ·
  <a href="#라이선스">라이선스</a> ·
  <a href="#사용-환경">사용 환경</a>
</p>

cutmaru는 방송 영상의 한국어 대본을 만들고, 앞뒤 맥락을 포함한 장면 후보를 보여준다. 편집자는 후보를 눌러 원본으로 이동하고, 채택한 구간을 정리해 유튜브 편집에 사용한다.

## 다운로드

Windows x64 프리릴리즈는 [GitHub Releases](https://github.com/ops-jaeha/cutmaru-releases/releases)의 **Assets**에서 받을 수 있다. 설치 파일과 확인용 SHA-256 파일, 해당 버전의 검증 범위를 제공한다.

## 빠른 시작

1. Windows 설치 파일을 실행하고 앱을 연다.
2. 운영자가 발급한 라이선스 키를 입력하고 한국어 모델을 내려받는다.
3. SOOP에서 확보한 원본 MP4를 열고 분석을 시작한다.
4. 후보, 대본 검색과 썸네일을 확인한다. 시청자가 원본 기준으로 남긴 시간이 있다면 붙여넣는다.
5. 채택한 구간을 저장한다. Premiere Pro는 프리미어 XML을, DaVinci Resolve는 아래 편별 XML을 사용한다.

## 라이선스

앱을 사용하려면 운영자가 발급한 **라이선스 키**를 활성화해야 한다. 최초 활성화와 갱신에는 인터넷이 필요하다. 모델을 준비하고 라이선스를 활성화하면 유효기간 안에서는 오프라인으로 영상 분석을 할 수 있다.

## VOD 채팅

0.1.1 이상에서는 [SOOP 채팅 다운로더](https://chromewebstore.google.com/detail/glgejppjgdpfmkbddolbagcdieapigik)에서 저장한 TXT를 **VOD 채팅 가져오기**로 열 수 있다. 원본 영상과 채팅 시간이 다르면 시간 보정을 지정한다. cutmaru는 반응을 시간별로 집계해 후보로 보여준다.

영상, 대본과 채팅은 PC에 저장된다. 라이선스 서버에는 키 활성화 또는 갱신에 필요한 정보만 전송한다.

## 사용 환경

| 항목 | 안내 |
| --- | --- |
| 운영체제 | Windows x64 대상. 버전별 검증 환경은 릴리즈 노트 참조 |
| 그래픽카드 | 호환 GPU에서 가속 가능. CPU 전용 PC에서도 분석 가능 |
| 입력 | 로컬 SOOP 원본 MP4 |
| 인터넷 | 첫 모델 다운로드, 라이선스 활성화 및 갱신에 사용 |
| 편집 프로그램 | 앱 안에서 원본과 후보 검토 가능. Premiere Pro 및 DaVinci Resolve용 XML 내보내기 |

## 설치 파일 확인

설치 파일과 함께 받은 `SHA256SUMS.txt`의 값을 아래 명령의 결과와 비교할 수 있다. `cutmaru-setup.exe`에는 실제로 다운로드한 설치 파일 이름을 넣는다.

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\cutmaru-setup.exe'
```

릴리즈별 사용 범위와 서드파티 고지는 다운로드 페이지와 함께 제공한다.

## DaVinci Resolve에서 열기

1. cutmaru에서 컷을 채택하고 각 컷의 편과 순서를 정한다.
2. **DaVinci Resolve 1편 XML** 또는 **DaVinci Resolve 2편 XML**을 눌러 편별 파일을 저장한다.
3. Resolve에서 **File → Import → Timeline**으로 XML을 연다. 원본을 못 찾으면 같은 MP4를 Media Pool에 추가하거나 원본 폴더를 지정한다.

[DaVinci Resolve 설명서](https://documents.blackmagicdesign.com/UserManuals/DaVinciResolveReferenceManual.pdf)

## 편집용 자막

편집용 SRT가 포함된 버전에서는 **편집 1편 자막 SRT** 또는 **편집 2편 자막 SRT**로 채택한 컷에 맞춘 자막을 저장한다. 같은 편의 편집 타임라인 시작점에 SRT를 배치한다. **대본 SRT**는 원본 시간 기준이다.

## SOOP 링크와 편집 MP4

- **다운로드하고 1차 컷 만들기**에 SOOP 플레이어 주소를 입력하고 저장 위치를 정한다. 지원되는 공개 VOD의 영상 파트를 하나로 합치고, 댓글 타임스탬프와 대본 분석으로 단일 초벌 타임라인을 만든다. 로그인·구독 등 별도 권한이 필요한 영상은 SOOP에서 받은 MP4를 연다. 재생 채팅은 TXT 또는 CSV를 가져온다.
- 원본을 보며 현재 위치에서 컷을 추가하거나 나눌 수 있다. 후보별로 시작과 끝, 채택 여부, 편 번호와 순서를 수정한다.
- **편집 1편 MP4** 또는 **편집 2편 MP4**는 채택한 컷을 연결한다. **컷 사이 TV 노이즈 화면·효과음**을 켜면 원본 위치가 6초 이상 바뀌는 컷 사이에 0.2초 전환을 넣는다. XML과 편집용 SRT는 컷 타임라인 기준이다.

## 화면 모드

**설정 → 화면 모드**에서 **시스템 설정 따르기**, **다크**, **라이트**를 선택한다. 선택은 다음 실행에도 유지된다. 편집 타임라인의 컷을 누르면 원본에서 해당 위치로 이동한다.
