# 보고서

#### 1. 어려웠던 점
+ 우분투 설치 과정에서 큰 문제 없이 잘 진행되었다. 
+ ROS2 Jazzy를 설치하는 과정에서 uninstall까지 터미널에 입력해서 다 설치한걸 한 번 지웠었다.
+ VScode를 설치했는데 설치한 앱이 바로 나오지 않고 '앱 표시'에서 설치한 앱을 열어야 했었다. 
------------------------------
#### 2. 추가적으로 설정한 것
+ 한글 키보드 설정
+ 터미네이터 설치
  + ctrol + shift + o/e -> 창 세로/가로로 늘어남
  + ctrol + shift + w -> 창 삭제
-------------------------------
#### 3. 우분투/ros2를 설치하는 이유
+ 우분투를 설치한 이유
  + window보다 하드웨어/소프트웨어 작업하기 편하다.
+ ros2를 설치한 이유
  + ros2를 설치할 때, 터미널을 2개 열어서 서로 통신이 되는지 테스트를 했었다. 이런 통신을 위해 ros2를 설치한다.
  + 다른 사람들이 이미 만들었던 코드 등을 활용할 수 있다. 
-------------------------------
#### 4. git 이해한 것
+ git을 왜 써야할까?
  + 코드를 작성할 때 수정하는 과정에서 이전 코드를 다시 불러오고싶을 때, 본인이 했던 커밋을 확인하여 편리하게 코드를 수정할 수 있다.
  + 코드를 수정할 때, 원본 코드를 건드리지 않고 복사본을 수정하여 안전하게 코드를 수정할 수 있도록 한다. (git branch로 복사본을 만들어서 테스트)
  + 현재 내 상황을 git에 작성하여 다른 사람이 내 git을 보고 이해할 수 있도록 한다.
+ 왜 add와 commit을 나눠놨을까?
  + 전체적인 흐름 : 코드 수정 -> add -> commit 
  + add : 수정한 파일 중, 이번 커밋에 포함할 파일들을 목록에 올린다.
  + commit : 목록에 올라간 파일들을 저장하여 기록한다.
+ 기본 개념
  + 디렉터리 : window에서는 파일이라고 부르지만, 리눅스나 우분투에서는 디렉터리라고 부른다고 한다.
+ git branch
  + 한 코드로 여러명이 건드릴 때, branch를 이용하여 여러명이서 한 코드를 수정할 수 있도록 한다.
+ 자주 나오는 명령어
  + cd : 폴더의 이동을 표현할 때 사용
    + cd git_practice -> 폴더 안으로 이동
    + cd .. -> 상위 폴더로 이동
    + ~cd -> 홈 디렉터리로 이동
  + git log : 커밋 기록 확인
  + git diff : 수정했을 때, 이 전과 어떤 부분이 달라졌는지 비교
    + j/k 키로 스크롤, q로 종료
  + git branch <> : 복사본 만들기
  + git switch <> : 해당 브랜치로 이동
  + git merge <> : 메인 코드에 합치기
  + git restore <> : add하지 않은 수정사항 취소
  + git reset : 이미 commit한 것을 전으로 되돌리기
  + git status : 현재 디렉터리의 변화를 보여줌
--------------------------------
#### 5. git 실습
1. txt파일 만든 후, 수정 -> add -> commit 해보기
  + cd ~ //홈 디렉터리로 이동
  + mkdir git_practice //git-practice라는 이름의 새 폴더 생성
  + cd git_practice //생성한 폴더로 이동
  + git init //폴더를 git저장소로 지정
    + 일반 폴더는 내용을 수정하거나 삭제해도 현재의 상태를 나타내지만, git저장소는 언제 파일이 만들어지고, 수정되고, 삭제되는지 기록이 남는다.
  + echo "Hello Git!" > test.txt //출력할 글자를 test.txt로 보냄.
    + echo는 c언어에서 printf와 같은 역할을 한다.
  + git status//상태 확인
  <img width="1592" height="427" alt="스크린샷 2026-09-02 03-10-40" src="https://github.com/user-attachments/assets/1ae5481a-2366-4efe-9fac-f3fcf0c552f8" />
  test.txt가 빨간색으로 떠있다. -> git이 새 파일이 생겼음을 감지함.
  + git add test.txt//add
  <img width="1413" height="277" alt="스크린샷 2026-09-02 03-50-03" src="https://github.com/user-attachments/assets/76d514a6-b8b4-4ab8-98f9-7d6b5fc547f3" />
  test.txt가 초록색으로 떠있다. -> 커밋할 준비가 됨.
  + git commit -m "첫 번째 파일 생성"//commit
  + git log --oneline//커밋 기록 확인
  <img width="1274" height="178" alt="스크린샷 2026-09-02 04-03-37" src="https://github.com/user-attachments/assets/2258b6b4-9e51-4411-9306-2b9d64353b21" />

2. branch 해보기
  <img width="1089" height="282" alt="Screenshot from 2026-09-02 17-58-54" src="https://github.com/user-attachments/assets/f3b2280a-e8ef-4a06-a078-2fdaf84c566d" />
  + git branch<>//test3복사본 생성
  + git branch//test3복사본이 잘 생성되었는지 확인
  + git switch test3//해당 branch로 이동
  + echo "김선우김선우김선우" >> test.txt
  + git add test.txt
  + git commit -m "test3 branch 연습하기"
  + git switch master
  + cat test.txt//아직 합치기 전이므로 이전 txt가 나온다.
  + git merge test3
  + cat test.txt//이제 김선우김선우김선우가 나온다.

