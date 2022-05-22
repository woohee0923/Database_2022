## 프로젝트 주제 : 쇼핑몰 주문목록 관리 페이지
-C (저장) : 회원이 주문한 상품 이름과 개수 저장  
-R (검색) : 상품을 주문한 회원 아이디와 상품 남은 수량 검색  
-U (업데이트) : 새로운 상품을 목록에 업데이트, 회원이 상품 개수 수정 요청 시 업데이트  
-D (삭제) : 배송이 완료된 회원의 주문내역 삭제 

## ERD
![프로젝트_0329_ERD](https://user-images.githubusercontent.com/81346143/168478125-cca8e05b-b989-4ab5-86fc-892e343ca287.png)  

## ERD 키 표시
![프로젝트_0405_ERD_키표시](https://user-images.githubusercontent.com/81346143/168478136-03d09f74-2539-42c7-823b-aadba7dcdf9c.png)  

## 프로그램 명세서 작성
1. **쇼핑몰회원**으로 가입하려면 ~~아이디~~, ~~비밀번호~~, ~~고객명~~, ~~주소~~, ~~전화번호~~를 입력해야 한다.
2. 가입한 회원에게는 ~~회원등급~~, ~~구매횟수~~, ~~포인트~~가 부여된다.
3. 회원은 아이디로 식별한다.
4. **옷**에 대한 ~~사이즈~~, ~~개수~~, ~~색깔~~, ~~가격~~, ~~제품번호~~를 유지해야 한다.
5. 옷은 제품번호로 식별한다.
6. 회원은 여러 개의 옷을 구매할 수 있고, 하나의 옷을 여러 회원이 구매할 수 있다.
7. 회원이 옷을 장바구니에 담으면 옷에 대한 ~~총액~~, ~~수량~~, ~~등록일자~~, ~~상품번호~~를 유지해야 한다.
8. 회원은 여러 개의 옷을 장바구니에 담을 수 있고, 여러 개의 옷은 여러 회원이 장바구니에 담을 수 있다.
9. 회원이 옷을 구매하면 구매한 옷에 대한 ~~구매번호~~, ~~주문총액~~, ~~결제방식~~, ~~구매일자~~를 유지해야 한다.
10. 옷은 여러 개의 **공장**이 공급하고, 하나의 공장은 여러 옷을 공급할 수 있다.
11. 공장에서 옷이 공급되면 옷에 대한 ~~구매가격~~, ~~수량~~, ~~구매일자~~를 유지해야 한다.
12. 공장에 대한 ~~공장명~~, ~~위치~~, ~~제품번호~~, ~~전화번호~~를 유지해야 한다.
13. 공장은 공장명으로 식별한다.
14. 옷이 배달되면 **배달원**의 ~~업체명~~, ~~담당자명~~, ~~전화번호~~를 유지해야 한다.
15. 배달원은 전화번호로 식별한다.
16. 옷은 한 명의 배달원이 운송하고, 한 명의 배달원은 여러 옷을 운송할 수 있다.
17. 배달원은 한 명의 회원에게 운송하고, 한 명의 회원은 하나의 배달원에게 운송받을 수 있다.
18. 회원이 **게시글**을 작성하면 글의 ~~작성일자~~를 유지해야 한다.
19. 게시글에 대한 ~~게시글 번호~~, ~~아이디~~, ~~글~~을 유지해야 한다.
20. 게시글은 게시글 번호로 식별한다.
21. 회원은 여러 개의 글을 작성할 수 있고, 하나의 게시글은 한 명의 회원만 작성할 수 있다. 
--- 
단일 속성: 회원(아이디), 회원(PW), 회원(고객명), 회원(회원등급), 회원(구매횟수), 회원(포인트), 게시글(게시글 번호), 게시글(아이디), 옷(개수), 옷(가격), 옷(제품번호), 옷(사이즈), 옷(색깔), 공장(공장명), 공장(위치), 공장(제품번호), 공장(전화번호), 배달원(업체명), 배달원(담당자명)  
다중 속성: 회원(주소), 회원(전화번호), 게시글(글), 배달원(전화번호)  
단순 속성: 회원(아이디), 회원(PW), 회원(고객명), 회원(회원등급), 회원(전화번호), 회원(구매횟수), 회원(포인트), 게시글(게시글 번호), 게시글(아이디), 게시글(글), 옷(사이즈), 옷(개수), 옷(색깔), 옷(가격), 옷(제품번호), 공장(공장명), 공장(제품번호), 공장(전화번호), 배달원(업체명), 배달원(담당자명), 배달원(전화번호)  
복합 속성: 회원(주소), 공장(위치)  
유도 속성: 회원(회원등급), 옷(가격)  

---
 
| 관계 | 참여하는 개체 | 관계 유형 | 속성 | 
|:---:|:---:|:---:|:---| 
| 작성 | 회원(선택), 게시글(필수) | 일대다 | 작성일자 |
| 장바구니 | 회원(선택), 옷(선택) | 다대다 | 총액, 수량, 등록일자, 상품번호 |
| 구매 | 회원(선택), 옷(선택) | 다대다 | 구매번호, 주문총액, 결제방식, 구매일자 |
| 운송 | 배달원(선택), 옷(필수) | 일대다 |  |
| 운송 | 배달원(필수), 회원(필수) | 일대일 |  |
| 공급 | 옷(선택), 공장(선택) | 다대다 | 구매가격, 수량, 구매일자 |

## E-R 모델
![1](https://user-images.githubusercontent.com/81346143/169702217-0c6bd1fb-7158-4117-968f-6423d91aa7eb.png)  

## 릴레이션 스키마 문서
![2](https://user-images.githubusercontent.com/81346143/169702233-0e457157-d88a-4e41-bcf2-c92af0cd305f.png)  
![3](https://user-images.githubusercontent.com/81346143/169702241-fbcf19aa-75c9-444f-81ec-8fc38514f36a.png)  

## 물리적 스키마 문서
![4](https://user-images.githubusercontent.com/81346143/169702244-aa211ed0-938c-4ed4-88e9-d7853559aa01.png)  
![5](https://user-images.githubusercontent.com/81346143/169702248-f5f9e5de-5d57-4991-9ede-793af46547b3.png)  

## 구현
![6](https://user-images.githubusercontent.com/81346143/169702258-319d2053-b1b5-424a-80a3-e98b41d4b4af.png)


