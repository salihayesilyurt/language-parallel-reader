# Language Parallel Reader

İngilizce–Türkçe paralel okuma ve dinleme aracı. Akademik metinleri paragraf paragraf okumak, sesli dinlemek ve kalıpları (collocation) öğrenmek için.

*A bilingual (English–Turkish) paragraph-by-paragraph reader with text-to-speech and collocation cards. Single HTML file, no server, no build step.*

## Özellikler
- İngilizce ve Türkçe metin yan yana, paragraf paragraf
- Sesli okuma: yalnız İngilizce, yalnız Türkçe, önce EN sonra TR, **cümle cümle EN/TR**
- Bir cümleye dokununca yalnızca o cümleyi okur; hız ayarı
- "Türkçeyi gizle": önce dinle, sonra kontrol et
- **PDF'ten içe aktarma**: İngilizce ve Türkçe PDF'i seçin; metin paragraflara ayrılır, başlıklar bölüm adı olur, şekil/tablo/denklem ve kaynakça atlanır, sayfa üst bilgileri temizlenir. Eklemeden önce metni düzenleyebilirsiniz.
- Kalıp kartları: anlam, yaygınlık, kullanım, alternatifler, örnek cümle. İngilizce metinde bir ifadeyi seçip kendi kartınızı ekleyebilir ya da hazır JSON paket yükleyebilirsiniz.
- Paketi JSON olarak indirme / kopyalama
- İlerleme (bitirilen paragraflar, öğrenilen kalıplar) tarayıcıda saklanır

## Kullanım
1. `index.html` dosyasını tarayıcıda açın ya da GitHub Pages ile yayınlayın (Settings → Pages → Branch: `main`, klasör: `/root`).
2. **Yeni metin ekle**: İngilizce ve Türkçe PDF'leri seçin ya da metni yapıştırın (paragraflar boş satırla, bölüm başlıkları `## Başlık` satırıyla ayrılır). Paragraf sayıları eşleşiyorsa EN–TR eşleşmesi hazırdır.
3. Ya da **JSON paket yükle** ile notlu/kalıplı bir paket açın.

Metinler yalnızca kullanıcının kendi tarayıcısında saklanır; hiçbir sunucuya gönderilmez.

## JSON paket biçimi
```json
{
  "title": "Başlık",
  "paragraphs": [
    {
      "sec": "1. Introduction",
      "en": "English paragraph...",
      "tr": "Türkçe paragraf...",
      "note": "İsteğe bağlı dil notu. <b>kalın</b>, <i>italik</i> ve <u>altı çizili</u> desteklenir.",
      "c": [
        {
          "p": "phrase exactly as it appears in the English text",
          "tr": "Türkçe anlamı",
          "f": 3,
          "u": "Kullanım notu",
          "alt": "Alternatifler",
          "ex": "Example sentence.",
          "src": { "t": "Kaynak adı", "u": "https://..." }
        }
      ]
    }
  ]
}
```
`f`: 3 = çok yaygın, 2 = yaygın, 1 = üslup tercihi / daha seyrek. `src` isteğe bağlıdır ve yalnızca doğrulanmış bir kaynak varsa eklenmelidir.

Örnek paket: `ornek-paket.json`.

## Notlar
- PDF okuma için [pdf.js](https://mozilla.github.io/pdf.js/) 3.11.174 cdnjs üzerinden ilk kullanımda yüklenir. Taranmış (görüntü) PDF'lerden metin çıkmaz. Paragraf ayırma sezgiseldir; iki sütunlu dergi düzenlerinde kontrol etmek gerekebilir.
- Ses, tarayıcının Web Speech API seslerini kullanır. Türkçe ses yoksa işletim sistemi ayarlarından eklenebilir.
- Telif hakkı: Yayımlanmış makale veya kitap bölümlerinin tam metnini herkese açık depoya koymayın. Paketleri yerelde tutup **JSON paket yükle** ile açın.

## Lisans
MIT
