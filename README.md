## 프로젝트 개요
건국대학교 2019 졸업프로젝트 과제로 2인 프로젝트로 진행되었습니다.

## 프로젝트 설명
Floating View를 이용해 노트북의 터치패드를 조작하듯이 화면 내의 커서를 조작하여<br>
한 손으로도 쉽게 핸드폰을 조작할 수 있도록 한 안드로이드 어플리케이션입니다.

## 사용언어
JAVA

## 주요 기능
* 커서 조작 <br>
   화면상의 터치패드에서 커서를 조작할 수 있습니다. <br>
   터치패드를 1번 클릭, 2번 클릭, 롱클릭에 각각 싱글터치, 뒤로가기, 롱터치 기능을 구현했습니다.<br>
   > OneHandService.java
   ```java
  final GestureDetector detector = new GestureDetector(this, new GestureDetector.SimpleOnGestureListener() {
            @Override
            public boolean onSingleTapConfirmed(MotionEvent e) {
                switch (curMode) {
                    case CLICK_MODE:
                        vibrator.vibrate(3);
                        int performCorX = cursorX + displayWidth / 2 + cursorWidth / 2;
                        int performCorY = cursorY + displayHeight / 2 + cursorHeight / 2;
                        performGesture(createSingleTapGesture(performCorX, performCorY));
                        break;
                    case MOVE_MODE:
                        break;
                }
                return super.onSingleTapConfirmed(e);
            }

            @Override
            public boolean onDoubleTap(MotionEvent e) {
                isModeChange = true;
                performGlobalAction(GLOBAL_ACTION_BACK);
                return super.onDoubleTap(e);
            }

            @Override
            public void onLongPress(MotionEvent e) {
                vibrator.vibrate(300);
                int performCorX = cursorX + displayWidth / 2 + cursorWidth / 2;
                int performCorY = cursorY + displayHeight / 2 + cursorHeight / 2;
                performGesture(createLongClickGesture(performCorX, performCorY));
                super.onLongPress(e);
            }
        });
  ```

## 추가 기능
* 터치패드 상단 드래그시 터치패드 이동 가능
* 우측 또는 좌측 하단에서 상, 하, 좌, 우 스와이프를 통해 터치패드 숨기기, 보이기, 서비스 종료 등 가능

## 맡은 역할
* 터치패드, 커서 뷰의 Floating View 생성 및 조작 기능 구현
* 싱글 터치, 롱 터치 등의 제스쳐 생성과 뒤로가기 등의 글로벌 액션 수행 기능 구현

## 실행화면
![image](https://user-images.githubusercontent.com/37248023/95209265-260b0280-0825-11eb-9af3-e749edf26127.png)
![image](https://user-images.githubusercontent.com/37248023/95209270-27d4c600-0825-11eb-9cfa-1c03704fe282.png)
