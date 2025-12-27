# Borusan AutoInsight

> **Borusan AutoHack** için geliştirilen bir hackathon projesi

Otomobil özellikleri ve teknik detayları hakkındaki soruları yanıtlamak için geliştirilmiş bir RAG (Retrieval-Augmented Generation) chatbot uygulaması. Sistem, PDF dokümanlarından otomotiv verilerini işleyerek OpenAI dil modelleri ile akıllı soru-cevap yetenekleri sunar.

## Özellikler

- **Doküman İşleme**: PDF dokümanlarından otomotiv verilerini çıkarır ve işler
- **Vektör Arama**: İlgili bilgileri bulmak için semantik benzerlik kullanır
- **LLM Entegrasyonu**: Yanıt üretimi için OpenAI GPT-3.5-turbo kullanır
- **Web Arayüzü**: Türkçe ve İngilizce sorguları destekleyen kullanıcı dostu Streamlit arayüzü
- **Gelişmiş RAG Teknikleri**: Cümle penceresi ve otomatik birleştirme yetenekleri içerir
- **Kalite Değerlendirmesi**: Yanıt uygunluğu ve kaynak doğruluğu için TruLens değerlendirmesi

## Desteklenen Araç Modelleri

- BMW 320i
- Mini Countryman
- Jaguar F-Pace
- Main_Data.pdf kaynağındaki diğer modeller

## Proje Yapısı

```
borusan-autohack/
├── borusan.py          # Ana Streamlit web uygulaması
├── utils.py            # Yardımcı fonksiyonlar ve gelişmiş RAG teknikleri
├── test.ipynb          # Geliştirme/test için Jupyter notebook
├── Main_Data.pdf       # Ana veri kaynağı (otomobil özellikleri)
├── eval_questions.txt  # Önceden tanımlanmış değerlendirme soruları
└── README.md           # Proje dokümantasyonu
```

## Gereksinimler

- Python 3.8+
- OpenAI API anahtarı

## Kurulum

1. **Depoyu klonlayın:**
   ```bash
   git clone https://github.com/yourusername/borusan-autohack.git
   cd borusan-autohack
   ```

2. **Bağımlılıkları yükleyin:**
   ```bash
   pip install streamlit llama-index openai python-dotenv trulens-eval nest_asyncio sentence-transformers huggingface-hub
   ```

3. **Ortam değişkenlerini ayarlayın:**
   Proje kök dizininde bir `.env` dosyası oluşturun:
   ```
   OPENAI_API_KEY=your_openai_api_key
   ```

## Kullanım

### Web Uygulamasını Çalıştırma

```bash
streamlit run borusan.py
```

Uygulama tarayıcınızda `http://localhost:8501` adresinde açılacaktır. Araç modelleri hakkındaki sorunuzu girin ve yanıt almak için "Sor" butonuna tıklayın.

### Jupyter Notebook Kullanımı

Geliştirme ve test için örnek sorgular ve yapılandırma ayarları içeren `test.ipynb` notebook'unu kullanabilirsiniz.

## Teknik Detaylar

### Uygulanan RAG Teknikleri

1. **Cümle Penceresi Sorgu Motoru**
   - Cümleleri 3 cümlelik bağlam penceresiyle gruplar
   - Daha geniş bağlam sağlayarak yanıt kalitesini artırır

2. **Otomatik Birleştirme Getirimi**
   - Çoklu parça boyutlarıyla hiyerarşik düğüm ayrıştırma (2048, 512, 128)
   - İlgili parçaları birleştirebilen akıllı getirme
   - Daha iyi sonuç sıralaması için Sentence Transformer yeniden sıralama

### Gömme Modelleri

- `BAAI/bge-large-en-v1.5`: Ana gömme modeli
- `BAAI/bge-small-en-v1.5`: Hafif alternatif
- `BAAI/bge-reranker-base`: Gelişmiş getirme için yeniden sıralama modeli

### Değerlendirme Metrikleri

Sistem, ölçüm için TruLens Eval kullanır:
- **Yanıt Uygunluğu**: Yanıtın soruyu karşılayıp karşılamadığı
- **Kaynak Doğruluğu**: Yanıtın kaynak materyalle desteklenip desteklenmediği

## Örnek Sorular

- BMW 320i'nin performans özellikleri nelerdir?
- Mini Countryman 2021 model özelliklerini karşılaştır
- Jaguar F-Pace'in bilgi-eğlence sistemi nasıl?
- BMW 320i bakım ipuçları nelerdir?

## Lisans

Bu proje eğitim ve demonstrasyon amaçlıdır.

## Katkıda Bulunma

Katkılarınızı bekliyoruz! Pull Request göndermekten çekinmeyin.
