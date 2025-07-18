# Capstone-Project
Analisis Berita Ekonomi Global Menggunakan Generative AI

# Project overview
Tujuan Proyek
Proyek ini bertujuan untuk membantu investor dalam memahami tren ekonomi global melalui analisis konten berita dari berbagai sumber ekonomi terpercaya. Dengan memanfaatkan kemampuan peringkasan berbasis Generative AI (IBM Granite), proyek ini mempermudah investor dalam memperoleh insight yang relevan dan mudah dipahami dari ribuan artikel ekonomi. Hasil peringkasan ini diharapkan dapat mendukung proses pengambilan keputusan investasi yang lebih cepat dan berbasis informasi.

# Latar Belakang
Dalam dunia investasi modern, informasi adalah aset utama. Setiap hari, ribuan artikel ekonomi dipublikasikan dengan cakupan isu seperti inflasi, suku bunga, geopolitik, dan perkembangan teknologi, yang semuanya dapat berdampak besar pada strategi investasi. Namun, membaca dan memahami seluruh informasi tersebut secara manual merupakan tantangan yang signifikan.
Generative AI menghadirkan solusi dengan kemampuannya dalam memahami dan merangkum teks dalam skala besar secara otomatis. Dengan menggunakan model IBM Granite, proyek ini mengeksplorasi bagaimana AI dapat menyaring dan menyajikan ringkasan dari artikel-artikel ekonomi, sehingga investor dapat memperoleh pemahaman makro dan mikroekonomi secara lebih efisien dan efektif.

# Permasalahan yang Diangkat
•	Investor kesulitan membaca ribuan artikel berita ekonomi secara cepat dan menyeluruh.
•	Informasi penting seperti topik utama, sentimen pasar, atau dampak ekonomi sering tersembunyi dalam artikel panjang dan tidak terstruktur.
•	Belum tersedia alat otomatis yang dapat secara akurat dan efisien meringkas konten berita ekonomi untuk membantu proses pengambilan keputusan investasi.

# Pendekatan Analisis Proyek (Langkah demi Langkah)
1. Persiapan Data
    •	Dataset: Financial Sentiment Categorized
    •	File diunggah ke Google Drive dan dimuat ke dalam Google Colab menggunakan pandas
    •	Dataset terdiri dari kolom: Title, Tag, Content, dan Category

2. Instalasi & Setup AI Model
    •	Library utama:
      o	langchain_community untuk integrasi LLM (IBM Granite)
      o	replicate untuk memanggil API Granite
    •	Token API disimpan secara aman menggunakan google.colab.userdata
    •	Model digunakan: ibm-granite/granite-3.3-8b-instruct via Replicate API

3. Pengambilan Sampel Artikel
    •	Dipilih secara acak 3 artikel dari dataset menggunakan .sample(3) untuk analisis mendalam (mewakili pendekatan proof of concept)
    •	Setiap artikel dianalisis melalui proses prompt yang beragam

4. Penerapan Prompt Generatif (Granite)
   Model IBM Granite digunakan dengan berbagai pendekatan prompt bertingkat (iteratif), antara lain:
   a. Prompt Dasar
      •	Prompt sederhana untuk menghasilkan ringkasan umum
      •	Format: “Summarize this financial news article”
   b. Prompt Ringkas Tiga Kalimat
      •	Format pendek untuk menguji kemampuan merangkum cepat dan padat
      •	Prompt: “Summarize in three sentences”
   c. Prompt Fokus Dampak Ekonomi
      •	Ringkasan diarahkan untuk menekankan dampak ekonomi dan kebijakan
      •	Format: “Summarize by focusing on economic impact and policy response”
   d. Prompt Terstruktur (Structured Summary)
      •	Format ringkasan dibagi menjadi bagian-bagian:
      • Main Events
      • Economic Indicators
      • Policy Implications
      • Market Impact
      • Recommendations
      •	Tujuannya agar hasil ringkasan mudah dibaca dan dianalisis
   e. Prompt Refined + Parameterisasi
      •	Prompt ditingkatkan dengan parameter khusus (top_k, top_p, max_tokens, dll.) untuk:
        o	Meningkatkan fokus isi
        o	Menghindari pengulangan
        o	Menjaga panjang ringkasan ideal
      •	Prompt juga diarahkan untuk menghasilkan insight dan rekomendasi eksplisit
5. Kompilasi dan Penyimpanan Hasil
    •	Output ringkasan dari tiap pendekatan disimpan kembali ke DataFrame dalam kolom berbeda (Granite_Summary, Granite_Refined_Summary, dll.)
    •	Hasil ini kemudian dijadikan dasar penyusunan insight dan rekomendasi investasi


Raw dataset link
https://www.kaggle.com/datasets/yogeshchary/financial-news-dataset (Financial_Sentiment_Categorized.csv)

Insight & findings
1. Sentimen Pasar Masih Dipengaruhi Faktor Kebijakan dan Pandemi
  •	Revisi pertumbuhan GDP AS ke atas memberikan sinyal positif terhadap pemulihan ekonomi pasca-COVID.
  •	Namun, pasar masih sangat sensitif terhadap keputusan moneter The Fed dan kebijakan stimulus.

2. Sektor Teknologi dan Ekspor Masih Rentan
  •	Saham-saham berbasis teknologi dan perusahaan dengan eksposur internasional (seperti Amazon) menunjukkan penurunan saat terjadi tekanan global.
  •	Pembukaan ekonomi secara bertahap di beberapa negara bagian menambah optimisme, tapi belum cukup kuat untuk mengangkat pasar secara keseluruhan.

3. Volatilitas Pasar Valas Masih Tinggi
  •	Dolar AS turun selama 5 sesi beruntun karena ketidakpastian kebijakan Fed.
  •	Proyeksi suku bunga dan arah stimulus menjadi faktor kunci bagi investor valuta dan komoditas.

AI Support Explanation
Dalam proyek ini, Generative AI digunakan untuk menganalisis dan meringkas berita ekonomi global, sehingga menghasilkan insight yang dapat membantu investor dalam pengambilan keputusan yang lebih cepat dan berbasis informasi.

Teknologi yang Digunakan:projek
•	IBM Granite Model (LLM - Large Language Model) melalui layanan Replicate API
•	Dijalankan di lingkungan Google Colab dengan integrasi Python dan LangChain

Fungsi AI dalam Proyek:
1.	Text Summarization (Abstractive & Structured)
AI merangkum artikel berita keuangan menjadi ringkasan padat, yang difokuskan pada:
  o	Peristiwa utama
  o	Indikator ekonomi
  o	Respons kebijakan
  o	Dampak terhadap pasar
  o	Rekomendasi untuk investor
2.	Prompt Engineering & Iterasi Ringkasan
Pendekatan peringkasan dilakukan melalui beberapa jenis prompt:
  o	Ringkasan umum (3 kalimat)
  o	Fokus pada dampak ekonomi
  o	Format analitik terstruktur
  o	Refined prompt dengan parameter (top_k, top_p, max_tokens) untuk menjaga kualitas output
3.	Multitask Output Generation
Model juga diarahkan untuk tidak hanya meringkas, tetapi memberikan analisis dan rekomendasi berbasis isi artikel.

Nilai Tambah AI:
•	Efisiensi: Meringkas artikel panjang dalam hitungan detik
•	Konsistensi: Output rapi, jelas, dan mudah dibandingkan antar artikel
•	Kontekstualisasi: AI memahami konteks ekonomi makro dan mikro dari artikel
•	Skalabilitas: Dapat diterapkan ke ratusan bahkan ribuan artikel secara otomatis
