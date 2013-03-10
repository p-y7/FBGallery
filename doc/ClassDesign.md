# FBGallery v1.0 클래스 설계
## 기능 명세
[Facebook](http://www.facebook.com) 의 사진첩에 저장되어 있는 이미지를 보여주는 기능을 구현한다.

1. facebook 인증 기능
1. facebook 계정에서 사진첩의 이미지 목록을 추출하는 기능
1. 비동기 이미지 다운로드 받아 표출할 수 있는 기능
1. facebook 인증 웹화면 등을 표출할 수 있는 웹뷰

> facebook 관련 기능은 SDK 검토 필요

## 컴포넌트
### Model
> facebook 관련 클래스 SDK 검토 필요

#### FBAuth
- 입력: facebook id/pw
- 출력: 인증 여부

#### FBPictureFinder
- 입력: facebook auth
- 출력: 이미지파일 정보 객체

#### YKAsyncDownloader
- 입력: 이미지파일 정보 객체
- 출력: 다운로드된 이미지 (비동기)

### View
#### YKImageView
- 입력: 이미지 경로 (또는 URL)
- 출력: 다운로드된 이미지

#### YKWebView
- 입력: URL
- 출력: 웹페이지

#### YKCollectionView
- 입력: 이미지 정보 객체
- 출력: 그리드방식의 이미지 출력 (비동기)

### Controller
#### FBAuthActivity
- 모델: FBAuth
- 뷰: YKWebView

#### FBImageViewActivity
- 모델: YKAsyncDownloader
- 뷰: YKImageView

#### FBCollectionViewActivity
- 모델: FBPictureFinder, YKAsyncDownloader
- 뷰: YKCollectionView
