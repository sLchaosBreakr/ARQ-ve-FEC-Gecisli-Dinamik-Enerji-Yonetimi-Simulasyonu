# ARQ-ve-FEC-Gecisli-Dinamik-Enerji-Yonetimi-Simulasyonu
Gürültülü Kablosuz Sensör  Ağlarında Adaptif Hata Kontrolü

## 👤 Öğrenci ve Üniversite Bilgileri
* **Ad Soyad:** Mustafa Selman UĞUZ
* **Öğrenci Numarası:** 22370031083
* **Üniversite:** Necmettin Erbakan Üniversitesi
* **Akademisyen:** Dr. Öğr. Üyesi Dr. HASAN SERDAR
* **Ders:** Kablosuz Algılayıcı Ağları

## 📌 Proje Hakkında
Bu proje, Kablosuz Sensör Ağları (WSN - Wireless Sensor Networks) ortamında yaygın olarak kullanılan hata kontrol mekanizmalarını (ARQ ve FEC) karşılaştırmalı olarak analiz etmek amacıyla geliştirilmiş, tarayıcı tabanlı interaktif bir simülasyondur. 

Projenin en öne çıkan özelliği, ortamdaki **Kanal Gürültüsü (BER - Bit Error Rate)** oranına göre sistemin protokoller arasında otonom olarak geçiş yapabilmesini sağlayan **Adaptif (Hibrit) Mod**'u barındırmasıdır. Simülasyon; başarı oranlarını (Throughput) ve radyo/CPU enerji maliyetlerini gerçek zamanlı olarak görselleştirerek kıyaslama imkanı sunar.

## 🚀 Protokoller ve Özellikler
* **ARQ (Automatic Repeat reQuest):** 
  * Hatalı iletimlerde alıcıdan tekrar gönderim (Retransmission) talep edilir.
  * Düşük gürültülü ortamlarda veri trafiğini düşük tuttuğu için enerji tasarrufu sağlar. Ancak gürültü arttığında sürekli tekrar gönderim döngüsüne girerek sistemi tıkar (NACK fırtınası).
* **FEC (Forward Error Correction):** 
  * Paketlere veri bütünlüğünü koruyan hata düzeltme kodları (Redundant Bits) eklenir. 
  * Eklenen bu kodlar paket boyutunu büyüttüğü için standart iletimden daha fazla radyo enerjisi ve CPU işlem gücü gerektirir. Ancak yüksek gürültülü ortamlarda paket kayıplarını, tekrar iletime gerek kalmadan alıcı tarafında düzeltebilir.
* **Adaptif (Hibrit) Mod:** 
  * Sistem, kanal gürültüsünü (BER: 0.015 eşik değeri) anlık olarak takip eder.
  * `BER < 0.015` (Düşük Gürültü): Minimum enerji tüketimi için otonom olarak **ARQ** protokolünü tercih eder.
  * `BER >= 0.015` (Yüksek Gürültü): Paket kayıplarını engellemek ve performansı korumak için anında **FEC** protokolüne geçiş yapar.

## 🖥️ Kullanıcı Arayüzü (UI) Özeti
Kullanıcı dostu arayüz 3 temel bölümden oluşur:

### 1. Üst Kontrol Paneli
* **Kanal Gürültüsü (BER) Slider:** Ortamdaki gürültü seviyesini anlık olarak artırıp azaltmanızı sağlar. Sistemlerin dayanıklılığını test etmek için ana araçtır.
* **Simülasyon Hızı:** Paket animasyonlarının akış hızını ayarlar.
* **Başlat/Durdur ve Sıfırla:** Simülasyonu kontrol eder ve sayaçları baştan başlatır.

### 2. Animasyon Paneli (Kanal Görselleştirme)
3 farklı iletişim kanalını (ARQ, FEC ve Adaptif) eş zamanlı olarak yarış Đhâlinde simüle eder. Paket durumları renklerle canlı olarak ifade edilir:
* 🟢 **Yeşil:** Başarılı İletim
* 🔴 **Kırmızı:** Gürültüden Bozuldu (Hata/Kayıp)
* 🟡 **Sarı:** Bozuldu ancak FEC kodları sayesinde kurtarıldı (FIX)
* ⚪ **Gri:** ARQ Tekrar İstek Paketi (NACK)

### 3. Gerçek Zamanlı Grafikler Paneli
* **Başarılı İletilen Paket (Throughput) Grafiği:** Hangi protokolün saniyede daha fazla sağlam paket ulaştırdığını çizgisel olarak gösterir. Yüksek gürültüde ARQ'nun çöktüğünü, FEC ve Adaptif modun ise hedefe ulaştığını görebilirsiniz.
* **Toplam Harcanan Enerji Grafiği:** Paket gönderim, alım ve CPU hata düzeltme maliyetlerini biriktirir. Adaptif modun düşük gürültüde ARQ kadar "cimri", yüksek gürültüde ise zorunlu olarak FEC kadar "bonkör" davrandığını kanıtlar.

## 🛠️ Nasıl Kullanılır?
1. Repoyu bilgisayarınıza klonlayın veya `.html` dosyasını indirin.
2. `wsn2.html` dosyasını herhangi bir modern web tarayıcısında (Chrome, Firefox, Safari vb.) çift tıklayarak açın. Herhangi bir sunucu kurulumuna gerek yoktur.
3. Simülasyonu başlatın ve **Kanal Gürültüsü (BER)** sürgüsüyle oynayarak protokollerin çevre şartlarına nasıl tepki verdiğini inceleyin.
