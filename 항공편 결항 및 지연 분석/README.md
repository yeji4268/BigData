# [항공기 결항 및 지연 요인 분석]

#### 학과 : 컴퓨터정보과 학번 : 202044050 이름 : 김예지
---
## 목차
[1. 분석 개요](#1-분석-개요)<br>
[2. 항공편 지연/결항 통계](#2-항공편-지연-결항-통계)<br>
[3. 항공편 지연/결항, 기상 상관관계 분석](#3-항공편-지연-결항-기상-상관관계-분석)<br>
[4. 항공편 지연 정비인력 분석](#4-항공편-지연-정비인력-분석)<br>
[5. 항공편 지연/결항, 항공기 기종별 상관관계 분석](#5-항공편-지연-결항-항공기-기종별-상관관계-분석)<br>


## 1. 분석 개요
* 배경 <br>
    [![plot.png](https://i.postimg.cc/59mpW9rz/plot.png)](https://postimg.cc/yWk0FKs6)<br>
    코로나 19의 영향으로 지난 2년 동안, 국내/외 여행의 수요가 대폭 감소하였지만, 최근 사회적 거리두기가 전면 해제된 이후로 위축됐던 여행 심리가 빠르게 되살아나면서 여행 수요가 점차 회복
* 목적 <br>
    항공편 이용의 변수 중 하나인 지연과 결항, 현재의 항공기 지연, 결항은 '통보' 수준. 이로 인해 이용객에게 가는 피해는 불가피. 항공기 지연 및 결항에 대한 피해를 최소화하는 것이 목적
* 기대효과<br>
    수집한 데이터에 대한 분석과 상관관계 분석, 더 나아가서 결항 예측까지 함으로써 이용객의 행동 결정에 도움을 줄 수 있을 것으로 기대

## 2. 항공편 지연 결항 통계
* 데이터 수집<br>
    + 지연 통계
        - 수집 : 데이터셋 다운로드
        - 수집 범위 : 2017년 1월 ~ 2021년 12월
        - 구분 : 국내선
        - 인천공항 지연통계 출처 : [인천국제공항공사](https://www.airport.kr/co/ko/cpr/statisticOfDelay.do)
        - 국내공항 지연통계 출처 : [한국공항공사](https://www.airport.co.kr/www/cms/frFlightStatsCon/delayStats.do?MENU_ID=1250#none)<br>
    + 결항 통계
        - 수집 : 데이터셋 다운로드
        - 수집 범위 : 2017년 1월 ~ 2021년 12월
        - 인천공항 결항통계 출처 : [인천국제공항공사](https://www.airport.kr/co/ko/cpr/statisticOfCanceled.do)
        - 국내공항 결항통계 출처 : [한국공항공사](https://www.airport.co.kr/www/cms/frFlightStatsCon/canceledStats.do?MENU_ID=1250)
    *한국공항공사에서는 인천공항의 지연통계를 제공하고 있지 않음

* 데이터 전처리 <br>
    - [지연 통계 : 데이터 전처리](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%2C%20%EC%A7%80%EC%97%B0%20%ED%86%B5%EA%B3%84/delayStats_Preprocessing.ipynb)
    - [결항 통계 : 데이터 전처리](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%2C%20%EC%A7%80%EC%97%B0%20%ED%86%B5%EA%B3%84/cancelStats_Preprocessing.ipynb)
* 데이터 시각화 & 분석 결과<br>
    + 지연 통계
        - 공항별 지연율 비교
        - 지연 요인 분석
        - [지연 통계 : 데이터 시각화 & 분석 결과](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%2C%20%EC%A7%80%EC%97%B0%20%ED%86%B5%EA%B3%84/delayStats_Visulization.ipynb)
    + 결항 통계
        - 공항별 결항률 분석
        - 결항 요인 분석
        - [결항 통계 : 데이터 시각화 & 분석 결과](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%2C%20%EC%A7%80%EC%97%B0%20%ED%86%B5%EA%B3%84/cancelStats_Visualization.ipynb)

## 3. 항공편 지연 결항, 기상 상관관계 분석
* 데이터 수집 : 크롤링 <br>
    + 시간별 기상 데이터 
        - 페이지 속성 : 정적 페이지 - pandas 사용
        - 수집 범위 : 2017년 1월 ~ 2022년 2월
        - 출처 : [항공기상청](https://amo.kma.go.kr/weather/stat/stat-hourly.do)
        - [기상 데이터 수집](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/weather_Crawling.ipynb)
    + 항공 스케줄 데이터
        - 페이지 속성 : 동적 페이지 - selenium 사용
        - 수집 범위: 2017년 1월 ~ 2022년 2월
        - 출처 : [항공정보포털시스템](https://www.airportal.go.kr/index.jsp)
        - [항공 스케줄 데이터 수집](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/schedule_Crawling.ipynb)
        *소스코드 일부 첨부
* 데이터 전처리
    + 시간별 기상 데이터
        - [기상 데이터 : 전처리](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/weather_Preprocessing.ipynb)
    + 항공 스케줄 데이터
        - [항공 스케줄 데이터 : 전처리](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/schedule_Preprocessing.ipynb)
    + 기상 데이터, 항공 스케줄 데이터 병합
        - [데이터 병합](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/data_Merging.ipynb)
* 데이터 분석 & 시각화
    + 항공 스케줄 분석
        - 지연 분석
            * 월별 지연 분석
            * 시간별 지연 분석
        - 결항 분석
            * 월별 결항 분석
            * 시간별 결항 분석
        - [항공 스케줄 : 지연, 결항 분석](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/schedule_Visualization.ipynb)
    + 병합 데이터 분석
        - [병합 데이터 분석](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/data_Visualization.ipynb)
    + 머신러닝을 이용한 데이터 분석
        - [의사결정나무](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/ML_Decision.ipynb)
        - [로지스틱 회귀](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/ML_Logistic.ipynb)
        - [SVM](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EA%B8%B0%EC%83%81%20%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84%20%EB%B6%84%EC%84%9D/ML_SVM.ipynb)
## 4. 항공편 지연 정비인력 분석
* 데이터 수집 
    - 항공 종사자 현황 데이터
        + 페이지 속성 : 다운로드
        + 수집 범위 : 2017년 1월 ~ 2021년 12월
        + 출처 : [국토교통부](https://stat.molit.go.kr/portal/cate/statView.do?hRsId=523&hFormId=4630&hSelectId=4630&hPoint=00&hAppr=1&hDivEng=&oFileName=&rFileName=&midpath=&month_yn=N&sFormId=4630&sStart=2017&sEnd=2021&sStyleNum=1003&EXPORT=)
    - 국내 항공사 지연/결항률 데이터
        + 페이지 속성 : 다운로드
        + 수집 범위 : 2017년 ~ 2021년
        + 출처 : [항공정보포털](https://www.airportal.go.kr/life/consumer/Con03-02-03.html?date=20210625)
* 데이터 전처리 
    - 항공 종사자 현황 데이터
        + [항공 종사자 현항 데이터 : 전처리](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EC%A0%95%EB%B9%84%EC%9D%B8%EB%A0%A5%20%EB%B6%84%EC%84%9D/mechanic_Preprocessing.ipynb)
    - 항공 종사자 데이터, 항공사별 지연/통계 데이터 병합 & 전처리
        + [데이터 병합 & 전처리](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EC%A0%95%EB%B9%84%EC%9D%B8%EB%A0%A5%20%EB%B6%84%EC%84%9D/airlineData_Preprocessing.ipynb)
* 데이터 분석 & 시각화
    - [통합 데이터 분석 & 시각화](https://github.com/yeji4268/BigData/blob/main/%ED%95%AD%EA%B3%B5%ED%8E%B8%20%EA%B2%B0%ED%95%AD%20%EB%B0%8F%20%EC%A7%80%EC%97%B0%20%EB%B6%84%EC%84%9D/%EC%A0%95%EB%B9%84%EC%9D%B8%EB%A0%A5%20%EB%B6%84%EC%84%9D/airlineData_Visualization.ipynb)