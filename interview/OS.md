# 1. 운영체제
## 운영체제
- 시스템의 자원과 동작을 관리하는 소프트웨어
- 프로세스, 저장장치, 네트워킹, 사용자, 하드웨어를 관리

## 메모리
 <img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/dbc5a1ca-19cb-4a79-834a-028483e5efe3" />

- 메모리 공간 종류 4가지: Code, Data, Heap, Stack
    - 코드는 소스코드가 들어감
    - data는 전역변수, 정적변수가 들어감
    - heap은 사용자가 직접 관리하는 영역 (데이터가 동적으로 들어감)
    - stack은 함수의 호출정보, 지역변수, 매개변수가 저장

 ## 프로세스, 스레드
 <img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/8ee8252f-5032-4f14-99eb-a592c561b16b" />

 - 프로세스: 실행중인 프로그램
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/4316e12d-b104-41e4-b283-e731f348b793" />

 - 스레드: 프로세스 안 실행 단위
 > 프로세스는 메모리와 CPU를 프로세스마다 할당받아서 사용하는데 스레드는 프로세스 안에서 프로세스 안에서 다른 스레드와 메모리, CPU를 공유해서 사용

## CPU 스케줄러
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/bf2f1d6e-a241-4fa2-a3de-a71cb4c163bf" />

- 각각의 프로그램들을 번갈아가면서 짧게 실행함
- 실행하고 있는 프로세스가 준비큐 안에 있음
- 프로세스의 CPU를 할당하는 방법
- 비선점
  - FCFS(first come first served)
    - 먼저 CPU를 요청하는 프로세스를 처리
  - SJF(shortest job first)
      - CPU 사용시간이 짧은 것을 가장 먼저 실행
- 선점
  - SRT(shortest remaining time)
    - 프로세스종료시간이 진행 중인 프로세스보다 처리 시간이 짧으면 sleep시키고 먼저 할당
  - RR(round robin)
    - 모든 프로세스를 공평하게 실행
    - 타임 퀀텀이 길면 FCFS와 다를 게 없음
    - 짧다면 옮길 때 비용이 발생하여 비효율적임
      - 타임 퀀텀을 적당히 조절하는 것이 좋음
  - priority scheduling(우선 순위 스케줄링)
    - 우선 순위에 따라 프로세스에 CPU를 우선 할당하는 방식
> 준비큐에 있는 프로세스에 대해서 CPU를 할당하는 방법입니다. FCFS, SJF, SRT, Priority Scheduling, Round Robin이 있습니다.

## 가상 메모리
- 사용하는 부분만 메모리에 올리고 나머지는 디스크에 보관
> 모든 프로세스에게 메모리를 할당하기에는 메모리의 크기가 한꼐가 있어서
> 사용하는 방법입니다. 프로세스에서 사용하는 부분만 메모리에 올리고 나머지는 디스크에 보관하는 기법을 가상메모리라고 합니다.

## 데드락
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/72ae92c1-179d-40f3-95e5-aa430961dd0a" />

- 프로세스가 자원을 얻지 못해 다음 작업을 못하는 상태
- 발생 조건
    1.  상호배제: 자원은 한 번에 한 프로세스만이 사용할 수 있어야 한다.
    2.  점유대기: 최소한 하나의 자원을 점유하고 있으면서 다른 프로세스에 할당되어 사용하고 있는 자원을 추가로 점유하기 위해 대기하는 프로세스가 있어야 함.
    3.  비선점: 다른 프로세스에 할당된 자원은 사용이 끝날 때까지 강제로 빼앗을 수 없어야 함.
    4.  순환대기: 프로세스의 집합에서 P0는 P1이 점유한 자원을 대기하고 P1은 P2가 점유한 자원을 대기하고 P2 ---Pn-1은 Pn이 점유한 자원을 대기하며 Pn은 P0가 점유한 자원을 요구해야 함.
> 데드락은 프로세스가 자원을 얻지 못해 다음 작업을 못하는 상태입니다. 예를 들어 P1, P2가 각각 자원 A와 B를 얻어야 되는데 P1이 A를 P2가 B를 가지고 있어 서로 무한정 기다리는 상태를 데드락이라고 합니다.
> 데드락은 다음의 네 가지 조건이 동시에 발생해야 성립이 가능한데요. 상호배제, 점유대기, 비선점, 순환대기입니다.

참고: [개발자 장고](https://www.youtube.com/watch?v=4ZyUAZ6Vrfc&list=PLi-xJrVzQaxU-xK2ao8utngQJqAX4DQty&index=2)