## HowDoYouFeel
딥러닝 프로젝트 컴퓨터비전을 통한 반려견 감정분석

### 프로젝트 배경
---

![강아지프로젝트배경](https://user-images.githubusercontent.com/86764734/177396725-79e889d0-364d-4e82-90ca-4e635545530a.png)

- 1인가구가 늘어나면서 반려견을 키우는 사람들이 늘어나고 있다.  나 또한 어렸을 때 반려견이 있었는데 귀엽고 사랑스럽지만 감정을 이해하고 파악하여 케어하는 것이 쉽지 않았던 기억이 있다. 몇 년 전부터 판매되었던 강아지 통번역기처럼 반려견의 표정을 통해 감정상태를 알려주는 서비스가 있다면 사람들의 호기심을 자극할 수 있지 않을까 생각되었다. 

### 프로젝트 목표

---

-강아지 이미지를 감정 별로 분류하여 딥러닝을  통해 감정분석

### 사용 프로그램

---

- HTML5 : 홈페이지 프레임 제작 (로그인, 회원가입, 검색, 키워드 관리 페이지)
- bootstrap : 구성요소 디자인
- Python (Flask) : 서버 연결 (Django보다 좀 더 가벼운 Flask 사용)
- ~~MySQL :  Flask-MySQL 라이브러리를 사용하여 웹과 DB를 연동하였다.~~
- ~~Javascript : 버튼 클릭 등 동적인 기능 구성~~
- 협업 도구로는 깃허브(Github)와 노션(Notion)을 사용
- heroku : 웹 배포

### 서비스 구성 및 제작 과정
---

**데이터파이프라인**

![Untitled (14)](https://user-images.githubusercontent.com/86764734/175530392-70de8f3a-72f3-4300-bb54-381eab8abddc.png)

**크롤링 코드 작성** : 구글 검색 결과를 크롤링 할 수 있는 코드 작성

- 표정 검색어를 통해 데이터 분류
    - happy, angry, sad, hurgry, amazed 각 키워드당 이미지 700개씩
- selenium 을 통한 html 파싱
- 스크롤 다운 + 결과 더보기 누르는 while문을 통해 검색 결과 모두 크롤링

**모델링 : 수집한 이미지 데이터를 기반으로 컴퓨터비전 진행**

- 데이터 전처리
    - Class 분류
    - 정규화
    
    ![Untitled (15)](https://user-images.githubusercontent.com/86764734/175530570-c4612c75-1eab-408b-84d1-e673472e7735.png)
    
    - 데이터 증강
    
    ![Untitled (16)](https://user-images.githubusercontent.com/86764734/175530641-312f49d7-5d77-4334-be45-c22c59d9bddc.png)
    
- 모델 선정
    - CNN (Val_Acc = 0.328)
    - ResNet50 (Val_Acc = 0.449)
    
- 하이퍼파라미터 튜닝 (Val_Acc = 0.524)
    - Early stopping
    - ModelCheckpiont

### 추후 발전 과제

---

- 모델 성능 향상
    - 모델을 훈련시킬 데이터의 수가 많지 않았기 때문에 모델의 성능이 높지 않았다고 생각되어 수가 데이터 수집 진행
    - 추가수집이 완료된다면 모델 하이퍼파라미터 튜닝을 통해 성능 개선
- 웹개발
    - Flask를 통해 기본적인 웹은 만들었으나 모델 웹서빙을 진행하지 못함
    - 모델 서빙을 마치고 구현하려했던 동적 웹페이지 구현 후 배포 진행
