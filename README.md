# 🧬 Lung Cancer Gene Prediction with Augmented Data Pre-training

본 프로젝트는 유전자 발현 데이터를 기반으로 폐암 아종을 분류하고,  
**데이터 증강과 2단계 학습(pre-training → fine-tuning)**을 활용하여  
딥러닝 모델의 성능을 개선한 연구 프로젝트입니다.

---

## 📌 Overview

고차원 유전자 데이터는 샘플 수가 적어 모델 학습에 한계가 존재합니다.  
본 연구에서는 데이터 증강을 통해 학습 데이터를 확장하고,  
증강 데이터의 영향을 최소화하기 위해 **2단계 학습 구조**를 설계했습니다.

---

## 📊 Dataset

| 항목 | 내용 |
|------|------|
| 데이터 | TCGA (The Cancer Genome Atlas) |
| 샘플 수 | 1,018명 |
| 변수 수 | 19,977개 유전자 |
| 특징 선택 | 암 관련 유전자 323개 선택 |
| 전처리 | log2 변환 + z-score 정규화 |

---

## ❗ Problem

- 고차원 데이터 대비 샘플 수 부족
- 데이터 부족으로 인한 모델 성능 한계
- 의료 데이터 특성상 단순 증강 데이터 사용의 어려움

---

## 💡 Method

### 1. Data Augmentation

유전자 데이터를 기반으로 새로운 샘플을 생성하기 위해  
통계 기반 데이터 증강 방법을 적용했습니다.

- 샘플 평균 기반 생성
- 클래스 기준 샘플링
- 혼합 샘플 생성

---

### 2. Two-stage Training

증강 데이터의 영향을 줄이기 위해  
다음과 같은 학습 구조를 설계했습니다.

#### Stage 1 (Pre-training)
- 원본 데이터 + 증강 데이터 사용
- 모델 초기 학습 수행

#### Stage 2 (Fine-tuning)
- 원본 데이터만 사용
- 최종 모델 학습

👉 증강 데이터의 장점은 활용하면서  
👉 최종 모델 왜곡은 최소화

---

## ⚙️ Experiment

- Stratified 10-fold Cross Validation
- 다양한 머신러닝 모델과 성능 비교
  - Logistic Regression
  - Random Forest
  - SVM
  - XGBoost / LightGBM
  - MLP (Deep Learning)

---

## 📈 Results

- 제안 모델 정확도: **88.32%**
- Baseline MLP 대비 약 **1% 성능 향상**

👉 소량 데이터 환경에서  
👉 데이터 증강 기반 학습의 효과 검증

---

## 📄 Paper

👉 [Pre-training with Augmentation Data in Deep Learning Model](./paper/lung_cancer_paper.pdf)

---

## 🧠 Key Takeaways

- 데이터 증강은 소량 데이터 문제 해결에 효과적
- 하지만 직접 학습에 사용 시 왜곡 가능성 존재
- **2단계 학습 구조가 이를 효과적으로 해결**
- 데이터 처리 기준보다  
  **데이터 활용 방식이 성능에 더 큰 영향을 줄 수 있음**

---

## 📁 Project Structure
