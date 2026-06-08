# 🔥 기상 및 인구 데이터를 활용한 대한민국 산불 발생 예측 및 시계열 분석
> **기상청/카카오맵 API 기반 다각적 EDA 및 시계열(ARIMA/Prophet) & 딥러닝(LSTM) 예측 모델 구축**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=Python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=TensorFlow&logoColor=white)
![Prophet](https://img.shields.io/badge/Prophet-8A2BE2?style=flat-square)
![Statsmodels](https://img.shields.io/badge/Statsmodels-蓝?style=flat-square)

---

## 1. 프로젝트 개요
### 배경 및 목적
* 기후 변화로 인해 산불 발생 빈도와 피해 규모가 전 세계적으로 급증하고 있으며, 국내 또한 대형 산불로 인한 사회·경제적 피해가 심각함
* 본 프로젝트는 **2016년부터 2025년까지의 국내 산불 발생 이력**을 바탕으로 기상 조건(온도, 습도, 풍속, 증발량), 미세먼지(PM10, PM2.5), 인구 밀도 등 다각적인 환경 요인을 결합하여 **산불 발생 패턴을 파악하고 향후 발생 건수를 선제적으로 예측**하는 인공지능 모델을 개발

### 주요 핵심 요약
* **복합 API 파이프라인**: 기상청 ASOS 공공 API 데이터와 카카오맵 공간 좌표 API 연동 가공
* **시계열정상성 확보**: ADF(Augmented Dickey-Fuller) 통계적 검정을 통한 데이터 정상성 분석 검증
* **다차원 모델 벤치마킹**: 전통 통계 시계열(ARIMA, SARIMA)부터 머신러닝(Prophet), 시계열 딥러닝(LSTM)까지 전방위 모델 비교 실험

---

## 2. 데이터 파이프라인 & 디렉토리 구조
프로젝트 전반에 걸친 정형화된 분석 파이프라인 관리를 위해 아래와 같이 모듈화하여 저장소를 구성했습니다.

```text
📁 EST_SECOND_Project
│
├── 📁 00 WildFire & Weather & particulate_matter & Population  # 원본 및 정제 데이터셋
│   ├── 📄 WildFire_20160101_20250425.csv
│   ├── 📄 WildFire_fixdata.csv
│   └── 📄 wildfire_daily_totals_region_metro_integrated.csv
│      # 그 외 데이터는 첨부하지 않았음.
├── 📁 01 Data Preparation & EDA                               # 데이터 수집 및 기획 분석
│   ├── 📄 kma_api_data_generation.ipynb (기상청 API 데이터 수집 및 병합)
│   ├── 📄 kakao_map_api_address_coords.ipynb (카카오맵 API 기반 위경도 매핑)
│   ├── 📄 wild_fire_eda_phase1.ipynb (산불 발생 기초 통계 분석)
│   ├── 📄 wildfire_eda_phase2.ipynb (통계적 시계열 패턴 및 정상성 검정)
│   └── 📄 weather_eda_features.ipynb (기상 변수 및 바람 데이터 특징 추출)
│
└── 📁 02 Modeling                                             # 예측 알고리즘 실험 룸
    ├── 📄 modeling_arima.ipynb (전통 선형 시계열 모델)
    ├── 📄 modeling_sarima.ipynb (계절성 반영 시계열 모델)
    ├── 📄 modeling_prophet.ipynb (트렌드·시즌성 머신러닝 모델)
    └── 📄 modeling_lstm.ipynb (순환 신경망 기반 시계열 딥러닝 모델)
