# 📊 UTS 2 Time Series Forecasting - LSTM vs ARIMA

### 👤 Nama: Paul Kusuma

### 🆔 NIM: 215314051

### 🎓 Mata Kuliah: Time Series Forecasting

### 🧪 Topik: Perbandingan Model LSTM dan ARIMA untuk Prediksi Kurs USD/IDR

---

## 📁 Dataset

- **Sumber**: Yahoo Finance (`USDIDR=X`)
- **Periode**: 01 Januari 2020 - 01 April 2024
- **Kolom digunakan**: `Close`
- **File CSV**: `usd_idr_preprocessed.csv`

---

## ⚙️ Langkah-Langkah Proyek

### 🔹 Preprocessing:

- Ambil kolom `Close`, ubah frekuensi menjadi harian (`asfreq('D')`)
- Isi missing value dengan `forward fill`
- Simpan dataset dalam format `.csv`

### 🔹 Model LSTM:

- Normalisasi data (`MinMaxScaler`)
- Split data: 30 hari terakhir sebagai data uji
- Sliding window (`window_size = 10`)
- Input reshape ke format 3D `[samples, timesteps, features]`
- Bangun model `Sequential` dengan `LSTM(50)` dan `Dense(1)`
- Latih model selama 30 epoch
- Evaluasi menggunakan MAE dan MSE
- Visualisasikan prediksi LSTM vs data aktual

### 🔹 Model ARIMA:

- Gunakan data asli tanpa normalisasi
- Model `ARIMA(5,1,0)`
- Prediksi 30 hari ke depan
- Evaluasi menggunakan MAE dan MSE
- Visualisasikan prediksi ARIMA vs data aktual

### 🔹 Plot Gabungan:

- Gabungkan LSTM, ARIMA, dan data aktual dalam satu grafik
- Tambahkan nilai evaluasi MSE dan MAE pada plot

---

## 📈 Hasil Evaluasi

| Model | MSE      | MAE   |
| ----- | -------- | ----- |
| LSTM  | 914.12   | 24.96 |
| ARIMA | 10320.18 | 82.06 |

---

## 🧠 Kesimpulan

Model **LSTM menunjukkan performa yang jauh lebih baik** dibanding ARIMA.

- MAE LSTM jauh lebih rendah, artinya prediksinya lebih dekat ke nilai aktual.
- MSE LSTM juga lebih rendah, menandakan model ini lebih tahan terhadap outlier.
- **LSTM unggul dalam mempelajari pola non-linear dan fluktuatif** seperti kurs mata uang.
- **ARIMA lebih cepat dan sederhana**, namun kurang akurat untuk pola kompleks.

Dua metode time series forecasting yaitu LSTM (Long Short-Term Memory) dan ARIMA (Autoregressive Integrated Moving Average) telah digunakan untuk memprediksi nilai tukar USD/IDR.
Hasil evaluasi menunjukkan bahwa:
LSTM memiliki MAE sebesar ~24.96 dan MSE sebesar ~914.12.
ARIMA memiliki MAE sebesar ~82.06 dan MSE sebesar ~10320.18.

Model LSTM menunjukkan performa yang lebih baik secara signifikan dibandingkan ARIMA dalam memprediksi nilai tukar USD/IDR.
MAE yang lebih rendah menunjukkan bahwa rata-rata kesalahan prediksi LSTM lebih kecil, sedangkan MSE yang jauh lebih rendah menandakan LSTM lebih tahan terhadap error besar atau outlier.

Ini membuktikan bahwa LSTM lebih unggul dalam menangkap pola non-linear dan fluktuasi kompleks pada data keuangan seperti kurs mata uang.
Di sisi lain, ARIMA lebih sederhana dan cepat dilatih, namun cenderung kurang akurat untuk dataset dengan pola yang tidak linear.
> Dengan performa ini, LSTM adalah model yang lebih cocok untuk forecasting kurs USD/IDR dibanding ARIMA.
