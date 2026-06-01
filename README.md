# Purwadhika Capstone Project Module 3
## Machine Learning Classification Project

## Overview
Sebuah perusahaan Asuransi Travel XYZ memberikan sebuah layanan asuransi untuk traveler yang ingin bepergian secara tenang untuk perjalanan domestik dan luar negeri. Beberapa negara mewajibkan traveler yang akan berkunjung untuk memiliki asuransi travel, terkhususnya negara-negara di Amerika dan Eropa.  

Memitigasi risiko liquiditas keuangan di mana perusahaan harus menyiapkan alokasi untuk traveler yang akan klaim asuransi dapat menjadi sebuah issue apabila perusahaan buta terhadap kemungkinan jumlah customers yang akan klaim asuransi. Bilamana perusahaan tidak menyiapkan alokasi yang cukup dan terjadi lonjakan dalam konteks jumlah traveler yang klaim asuransi yang melebihi ekspektasi perusahaan, perusahaan bisa berada dalam risiko tidak bisa memenuhi klaim asuransi tersebut.

## Problem Statement
Karena itulah, perusahaan Asuransi Travel XYZ berekspektasi untuk bisa memprediksi traveler yang akan klaim asuransi, supaya perusahaan memiliki gambaran (setidaknya gambaran kasar) untuk menentukan alokasi keuangan mereka.  
  
## Analytical Approach based on Data
Target (Label):  
0: Traveler that did not claim insurance  
1: Traveler that claimed insurance  

## Verdict and The Conclusion
LightGBM menjadi model final yang digunakan, karena model tersebut dapat menghasilkan output yang dapat diinterpretasikan sebagai berikut:  

- Dari 100 orang yang meng-klaim asuransi nya di REAL LIFE, 70 (70%) dari mereka dapat diprediksi oleh model tersebut (true positive), sementara 30 orang (30%) sisanya adalah orang-orang yang diprediksi tidak meng-klaim asuransi tetapi turns out meng-klaim asuransi (false negative).
- Sementara itu, mengukur dari seberapa presisi model yang telah dibuat. Dari 100 orang yang DIPREDIKSI meng-klaim asuransi, hanya 6 orang (6%) yang ternyata memang meng-klaim (true positive), dan sisanya 94 orang tidak meng-klaim (false positive).

## Cost Benefit Analysis

**Parameter asumsi biaya-biaya:**
- Total Pelanggan: 8.866 orang (sesuai test set)
- Total Klaim Aktual: 135 orang (1,53%) before model
- Average Premi (Net Sales): USD 40.55 per orang
- Average Commission fee: USD 9.7 per agency
- Average Pendapatan (Net Revenue): USD 30.85 per orang
- Kerugian (Biaya Klaim): USD 240 per klaim (USD 40 premium x 6) (https://www.squaremouth.com/press-room/travel-insurance-claims-paid-out-6x-policy-premium-in-2023)


**Cost-Benefit & Liquidity Risk Analysis**
| Metrik Operasional & Finansial | Before Model (Tanpa Prediksi) | After Model (Tuned LGBM) |
| :--- | :--- | :--- |
| **Total Pelanggan Dilayani (Test Set)** | 8,866 orang | 8,866 orang |
| **Pendapatan Bersih (Net Revenue)** | USD 273,072.80 <br>*(8,866 orang × USD 30.80)* | USD 273,072.80 <br>*(8,866 orang × USD 30.80)* |
| **Total Beban Klaim Aktual** | - USD 32,400.00 <br>*(135 kasus aktual × USD 240)* | - USD 32,400.00 <br>*(135 kasus aktual × USD 240)* |
| **PROFIT BERSIH (P&L)** | **USD 240,672.80** | **USD 240,672.80** |
| ----------------------------------------- | ----------------------------- | ----------------------------- |
| **METRIK MITIGASI RISIKO LIKUIDITAS** | ⚠️ **High Risk** (Blind) | ✅ **Managed Risk** (Prepared) |
| **Dana Klaim yang Berhasil Disiapkan** | **USD 0** | **USD 22,800.00** <br>*(True Positives: 95 × USD 240)* |
| **Risiko Kejutan Klaim (Gagal Antisipasi)**| **USD 32,400.00** <br>*(135 kasus)* | **USD 9,600.00** <br>*(40 kasus)* |
| **Status Kesiapan Budget** | 0% Siap <br>*(Terdampak Penuh)* | **70% Siap** <br>*(Risiko Terkontrol)* |
