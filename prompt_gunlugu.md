# Prompt Günlüğü — Uluslararası Futbol Maç Sonuçları Analizi

**Proje:** Veri Bilimi Final Projesi  
**Öğrenci:** Yiğit Delen — 1306230013  
**AI Aracı:** Claude AI  
**Yöntem:** Vibe Coding

---

## Açıklama

Bu günlük, proje geliştirme sürecinde Claude yapay zekâ asistanına yöneltilen önemli promptları kronolojik sırayla belgelemektedir. Her prompt için hangi geliştirme adımında kullanıldığı ve üretilen çıktı belirtilmiştir.

---

## Promptlar

---

### Prompt 1 — Veri Seti Seçimi
**Adım:** Planlama  
**Prompt:**
> "Spor analitiği temalı bir veri bilimi projesi yapacağım. Kaggle'da ücretsiz, kullanımı kolay, EDA ve modelleme yapmaya uygun bir futbol veri seti önerir misin?"

**Üretilen Çıktı:** "International Football Results (1872–2024)" veri seti önerildi. 49.000'den fazla maç içerdiği, CSV formatında olduğu ve doğrudan pandas ile okunabildiği belirtildi.

---

### Prompt 2 — Araştırma Sorularının Belirlenmesi
**Adım:** Proje Tasarımı  
**Prompt:**
> "Bu veri seti üzerinde sadece 'en fazlayı bul' türünden değil, gerçek bir hipotez içeren ve veriyle yanıtlanabilir araştırma soruları önerir misin? En az 4 tane olsun."

**Üretilen Çıktı:** Ev sahibi avantajı, gol trendi, tarafsız saha etkisi ve maç sonucu tahmini olmak üzere 4 araştırma sorusu belirlendi.

---

### Prompt 3 — Veri Yükleme ve İlk İnceleme
**Adım:** Veri Yükleme  
**Prompt:**
> "results.csv dosyasını yükleyip veri setinin genel yapısını gösteren kod yazar mısın? Kaç satır var, sütunlar ne, eksik değer var mı, genel istatistikler nasıl?"

**Üretilen Çıktı:** Veri yükleme ve ilk inceleme kodu oluşturuldu. Veri setinin 49.494 satır ve 9 sütundan oluştuğu, 13 eksik değer içerdiği görüldü.

---

### Prompt 4 — Veri Temizleme
**Adım:** Veri Temizleme  
**Prompt:**
> "Eksik değerleri temizle, 20'den fazla gol içeren maçları aykırı değer olarak çıkar, tarih sütununu düzgün formata çevir ve her adımı Türkçe yorum satırıyla açıkla."

**Üretilen Çıktı:** 13 eksik satır ve 9 aykırı maç veri setinden çıkarıldı. Tarih sütunu datetime formatına çevrildi. Temizleme sonrası 49.472 maçlık veri seti elde edildi.

---

### Prompt 5 — Maç Sonucu Sütunu Ekleme
**Adım:** Özellik Mühendisliği  
**Prompt:**
> "Her maç için ev sahibi mi kazandı, beraberlik mi oldu, deplasman mı kazandı bilgisini içeren yeni bir sütun nasıl eklerim?"

**Üretilen Çıktı:** `mac_sonucu()` fonksiyonu yazıldı ve `apply()` ile her satıra uygulandı. Ev sahibi galibiyeti, beraberlik ve deplasman galibiyeti sütunu oluşturuldu.

---

### Prompt 6 — Ev Sahibi Avantajı Analizi
**Adım:** EDA — Araştırma Sorusu 1  
**Prompt:**
> "Ev sahibi avantajını analiz ederken tarafsız sahada oynanan maçları dahil etmeli miyim? Kazanma oranlarını hesaplayıp görselleştiren kod yazar mısın?"

**Üretilen Çıktı:** Tarafsız maçların (neutral=True) analizden çıkarılması gerektiği açıklandı. Ev sahibi kazanma oranı %50.7, deplasman kazanma oranı %26.4 olarak hesaplandı. Pasta grafik ve çubuk grafik oluşturuldu.

---

### Prompt 7 — Gol Trendi Analizi
**Adım:** EDA — Araştırma Sorusu 2  
**Prompt:**
> "Yıllara göre ortalama gol sayısının nasıl değiştiğini gösteren bir grafik çizer misin? Yıllık dalgalanmayı düzeltmek için ne yapabilirim?"

**Üretilen Çıktı:** Yıllık ortalama gol hesaplandı, 5 yıllık hareketli ortalama eklendi. 1930–1970 arası 3.81 gol/maç, 2000–2024 arası 2.75 gol/maç olduğu bulundu.

---

### Prompt 8 — Tarafsız Saha Etkisi
**Adım:** EDA — Araştırma Sorusu 3  
**Prompt:**
> "Tarafsız sahada oynanan maçlarla normal maçları karşılaştıran bir grafik yazar mısın? Ev sahibi avantajı tarafsız sahada ne kadar değişiyor?"

**Üretilen Çıktı:** Normal maçlarda ev sahibi kazanma oranı %50.7, tarafsız sahada %44.2 bulundu. 6.6 puanlık fark gruplu çubuk grafikle görselleştirildi.

---

### Prompt 9 — Model Kurulumu
**Adım:** Modelleme  
**Prompt:**
> "Maç sonucunu tahmin eden bir sınıflandırma modeli kurmak istiyorum. Hangi modeli kullanmalıyım ve veriyi nasıl hazırlamalıyım? Metin sütunlarını nasıl sayıya çeviririm?"

**Üretilen Çıktı:** Random Forest sınıflandırma modeli önerildi. `LabelEncoder` ile turnuva adları sayıya çevrildi, veri %80 eğitim %20 test olarak bölündü.

---

### Prompt 10 — Model Eğitimi ve Değerlendirme
**Adım:** Modelleme  
**Prompt:**
> "Modeli eğitip test et. Doğruluk oranını ve hangi sonuçları iyi tahmin edip hangilerini edemediğini gösteren bir görsel ekler misin?"

**Üretilen Çıktı:** Random Forest modeli %46.9 doğrulukla eğitildi. Karmaşıklık matrisi ve özellik önemleri görselleştirildi.

---

### Prompt 11 — Model Performansını Yorumlama
**Adım:** Sonuç Analizi  
**Prompt:**
> "Model doğruluğu %46.9 çıktı, bu iyi bir sonuç mu? Raporda nasıl yorumlamalıyım?"

**Üretilen Çıktı:** 3 sınıflı bir problemde rastgele tahminin %33.3 olduğu açıklandı. Modelin bunu %13.6 puan geçtiği ve sınırlı özniteliklerle makul bir sonuç olduğu belirtildi.

---

### Prompt 12 — Kod Yorum Satırları
**Adım:** Dokümantasyon  
**Prompt:**
> "dropna() ve copy() fonksiyonlarının farkı nedir? axis=1 parametresi ne anlama geliyor? LabelEncoder tam olarak nasıl çalışıyor?"

**Üretilen Çıktı:** Her fonksiyonun ne işe yaradığı öğrenildi ve notebook hücrelerine Türkçe yorum satırları eklendi.

---

### Prompt 13 — README Dosyası
**Adım:** Dokümantasyon  
**Prompt:**
> "GitHub'a yükleyeceğim bir README dosyası lazım. Öğrenci bilgilerimi, veri kaynağını, kullanılan kütüphaneleri ve projeyi nasıl çalıştıracağımı içermeli."

**Üretilen Çıktı:** Öğrenci bilgileri, veri kaynağı ve lisans bilgisi, kütüphane listesi ve adım adım çalıştırma talimatlarını içeren README.md dosyası oluşturuldu.

---

### Prompt 14 — Rapor Yazımı
**Adım:** Raporlama  
**Prompt:**
> "Akademik raporda bulgular bölümünü yazarken her araştırma sorusunu ayrı alt başlık altında mı ele almalıyım? Sınırlamalar ve sonuç bölümlerine ne tür içerikler yazılır?"

**Üretilen Çıktı:** Rapor yapısı ve bölüm içerikleri hakkında bilgi alındı. Bulgular her araştırma sorusu için ayrı alt başlıkta, sınırlamalar ve sonuç bölümleri analiz bulgularına dayalı olarak yazıldı.

---

### Prompt 15 — Sonuçların Tutarlılığı
**Adım:** Hata Ayıklama  
**Prompt:**
> "Grafikteki yüzde ile koddaki yüzde birbirini tutmuyor, neden farklı çıkıyor? Nasıl düzeltirim?"

**Üretilen Çıktı:** Pasta grafiğin tüm maçları, özet kodunun ise yalnızca normal maçları kullandığı tespit edildi. Grafik `df_normal` kullanacak şekilde düzeltilerek tutarsızlık giderildi.

---

## Özet Tablosu

| # | Prompt Konusu | Adım |
|---|---------------|------|
| 1 | Veri seti seçimi | Planlama |
| 2 | Araştırma soruları belirleme | Tasarım |
| 3 | Veri yükleme ve ilk inceleme | Veri yükleme |
| 4 | Veri temizleme | Veri temizleme |
| 5 | Maç sonucu sütunu ekleme | Özellik mühendisliği |
| 6 | Ev sahibi avantajı analizi | EDA — Soru 1 |
| 7 | Gol trendi analizi | EDA — Soru 2 |
| 8 | Tarafsız saha etkisi | EDA — Soru 3 |
| 9 | Model kurulumu | Modelleme |
| 10 | Model eğitimi ve değerlendirme | Modelleme |
| 11 | Model performansını yorumlama | Sonuç analizi |
| 12 | Kod yorum satırları | Dokümantasyon |
| 13 | README dosyası | Dokümantasyon |
| 14 | Akademik rapor | Raporlama |
| 15 | Sonuçların tutarlılığı | Hata ayıklama |
