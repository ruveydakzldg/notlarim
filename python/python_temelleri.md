# Python Temelleri: Kapsamlı Çalışma Notları

Bu rehber, Python programlama dilinin temel yapı taşlarını pratik kod örnekleri ve açıklamalarla ele almaktadır.

---

## İçindekiler
1. [Değişkenler ve Veri Tipleri](#1-değişkenler-ve-veri-tipleri)
2. [Operatörler](#2-operatörler)
3. [Koşul Yapıları (if - elif - else)](#3-koşul-yapıları-if---elif---else)
4. [Döngüler (for & while)](#4-döngüler-for--while)
5. [Fonksiyonlar](#5-fonksiyonlar)
6. [Veri Yapıları (List, Tuple, Dict, Set)](#6-veri-yapıları-list-tuple-dict-set)
7. [Nesne Yönelimli Programlama (OOP) & Sınıflar](#7-nesne-yönelimli-programlama-oop--sınıflar)

---

## 1. Değişkenler ve Veri Tipleri

Python dinamik tipli (dynamically typed) bir dildir; yani bir değişken oluştururken veri tipini açıkça belirtmek gerekmez. Python atanan değere göre tipi otomatik belirler.

### Değişken Tanımlama Kuralları
- Harf veya alt çizgi (`_`) ile başlamalıdır, rakamla başlayamaz.
- Büyük/küçük harfe duyarlıdır (`yas` ile `Yas` farklıdır).
- Python anahtar kelimeleri (`for`, `if`, `def` vb.) değişken adı yapılamaz.
- Python topluluğunda değişkenler için genellikle `snake_case` kullanılır.

### Temel Veri Tipleri
- **`int`**: Tam sayılar (`10`, `-5`, `0`)
- **`float`**: Ondalıklı sayılar (`3.14`, `-0.01`)
- **`str`**: Metin (string) ifadeler (`"Merhaba"`, `'Python'`)
- **`bool`**: Mantıksal değerler (`True`, `False`)

```python
# Değişken atamaları
yas = 25                  # int
boy = 1.78                # float
ad = "Ruveyda"            # str
ogrenci_mi = True         # bool

# type() fonksiyonu ile veri tipini öğrenme
print(type(yas))          # <class 'int'>
print(type(boy))          # <class 'float'>
print(type(ad))           # <class 'str'>
print(type(ogrenci_mi))    # <class 'bool'>

# Tip Dönüşümleri (Type Casting)
str_sayi = "100"
sayi = int(str_sayi)      # str -> int (100)
ondalik = float(sayi)     # int -> float (100.0)
metin = str(sayi)         # int -> str ("100")
dogruluk = bool(0)        # 0 False, diğer sayılar True döner

# Çoklu atama ve f-string kullanımı
x, y, z = 1, 2, 3
print(f"{ad}, {yas} yaşında ve boyu {boy}m.")
```

---

## 2. Operatörler

Python'da verileri işlemek, karşılaştırmak ve mantıksal kontroller yapmak için çeşitli operatörler kullanılır.

### Aritmetik Operatörler
| Operatör | Anlamı | Örnek | Sonuç |
| :--- | :--- | :--- | :--- |
| `+` | Toplama | `5 + 2` | `7` |
| `-` | Çıkarma | `5 - 2` | `3` |
| `*` | Çarpma | `5 * 2` | `10` |
| `/` | Bölme (Her zaman float döner) | `5 / 2` | `2.5` |
| `//` | Tam Bölme (Taban bölme) | `5 // 2` | `2` |
| `%` | Modül (Bölümden kalan) | `5 % 2` | `1` |
| `**` | Üs Alma | `5 ** 2` | `25` |

### Karşılaştırma Operatörleri
Sonuç her zaman `bool` (`True` / `False`) döner.
- `==` : Eşit mi?
- `!=` : Eşit değil mi?
- `>`  : Büyüktür
- `<`  : Küçüktür
- `>=` : Büyük veya eşit mi?
- `<=` : Küçük veya eşit mi?

### Mantıksal Operatörler
- `and`: İki koşul da `True` ise `True`
- `or` : En az bir koşul `True` ise `True`
- `not`: Koşulun tersini alır (`not True` -> `False`)

### Atama, Üyelik ve Kimlik Operatörleri
```python
# Atama operatörleri
sayi = 10
sayi += 5   # sayi = sayi + 5 (15)
sayi *= 2   # sayi = sayi * 2 (30)

# Üyelik operatörleri (in, not in)
meyveler = ["elma", "armut", "muz"]
print("elma" in meyveler)      # True
print("kiraz" not in meyveler) # True

# Kimlik operatörleri (is, is not - bellek adresi kontrolü)
a = [1, 2]
b = [1, 2]
c = a

print(a == b)  # True (Değerleri aynı)
print(a is b)  # False (Bellek adresleri farklı)
print(a is c)  # True (Aynı nesneyi referans alıyorlar)
```

---

## 3. Koşul Yapıları (if - elif - else)

Koşul yapıları, program akışını belirli şartlara göre yönlendirmek için kullanılır. Python'da bloklar **girintileme (indentation - 4 boşluk)** ile belirlenir.

```python
not_ortalamasi = 78

if not_ortalamasi >= 85:
    harf_notu = "AA"
elif not_ortalamasi >= 70:
    harf_notu = "BB"
elif not_ortalamasi >= 50:
    harf_notu = "CC"
else:
    harf_notu = "FF"

print(f"Notunuz: {harf_notu}")

# İç İçe (Nested) Koşullar
yas = 20
ehliyet_var_mi = True

if yas >= 18:
    if ehliyet_var_mi:
        print("Araç kullanabilirsiniz.")
    else:
        print("Yaşınız tutuyor fakat ehliyetiniz yok.")
else:
    print("Yaşınız 18'den küçük.")

# Tek Satırlık Koşul (Ternary Operator)
durum = "Geçti" if not_ortalamasi >= 50 else "Kaldı"
print(f"Durum: {durum}")
```

---

## 4. Döngüler (for & while)

Döngüler, belirli bir kod bloğunu tekrarlı olarak çalıştırmak için kullanılır.

### `for` Döngüsü
Genellikle belirli bir aralıkta veya bir koleksiyonun (liste, string, demet vb.) elemanları üzerinde gezinmek için tercih edilir.

```python
# range(başlangıç, bitiş, artış_miktarı) - Bitiş değeri dahil değildir!
for i in range(1, 6):
    print(f"Sayı: {i}")

# Liste üzerinde gezinme
diller = ["Python", "JavaScript", "Go"]
for dil in diller:
    print(f"Programlama dili: {dil}")

# enumerate() ile hem indekse hem elemana erişme
for indeks, dil in enumerate(diller, start=1):
    print(f"{indeks}. Dil: {dil}")
```

### `while` Döngüsü
Belirtilen koşul `True` olduğu sürece çalışmaya devam eder. Sonsuz döngüye düşmemesi için koşulu değiştiren bir mekanizma içermelidir.

```python
sayac = 0
while sayac < 3:
    print(f"Sayaç: {sayac}")
    sayac += 1
```

### Döngü Kontrol İfadeleri: `break`, `continue`, `pass`
- `break`: Döngüyü tamamen sonlandırır.
- `continue`: O anki adımı atlayıp bir sonraki döngü adımına geçer.
- `pass`: Henüz kod yazılmamış yerlerde sözdizimi hatası almamak için yer tutucu olarak kullanılır.

```python
# break ve continue örneği
for numara in range(1, 10):
    if numara == 3:
        continue  # 3'ü ekrana basmadan atlar
    if numara == 7:
        break     # 7'ye geldiğinde döngüyü tamamen durdurur
    print(numara, end=" ")
# Çıktı: 1 2 4 5 6
```

---

## 5. Fonksiyonlar

Fonksiyonlar, belirli bir görevi yerine getiren ve tekrar tekrar çağrılabilen modüler kod bloklarıdır. `def` anahtar kelimesiyle tanımlanırlar.

### Temel Fonksiyon ve Parametreler
```python
def selamla(kullanici_adi="Misafir"):
    """Kullanıcıya karşılama mesajı döner."""
    return f"Hoş geldin, {kullanici_adi}!"

# Fonksiyon çağırma
mesaj1 = selamla("Ahmet")
mesaj2 = selamla() # Varsayılan parametre kullanılır
print(mesaj1)  # Hoş geldin, Ahmet!
print(mesaj2)  # Hoş geldin, Misafir!
```

### Esnek Argümanlar: `*args` ve `**kwargs`
- `*args`: Sayısı belirsiz konumsal (positional) argümanları tuple olarak alır.
- `**kwargs`: Sayısı belirsiz anahtar kelime (keyword) argümanlarını dictionary olarak alır.

```python
def toplami_bul(*sayilar):
    toplam = 0
    for s in sayilar:
        toplam += s
    return toplam

print(toplami_bul(2, 4, 6, 8)) # 20

def kullanici_profili(ad, **ekstra_bilgiler):
    print(f"Kullanıcı: {ad}")
    for anahtar, deger in ekstra_bilgiler.items():
        print(f" - {anahtar}: {deger}")

kullanici_profili("Zeynep", sehir="İstanbul", meslek="Mühendis")
```

### Lambda (Anonim) Fonksiyonlar
Tek satırda tanımlanan küçük ve isimsiz fonksiyonlardır. `lambda parametreler: ifade` formatındadır.

```python
kare_al = lambda x: x ** 2
print(kare_al(5)) # 25

sayilar = [1, 2, 3, 4, 5]
kareler = list(map(lambda x: x**2, sayilar))
ciftler = list(filter(lambda x: x % 2 == 0, sayilar))
print("Kareler:", kareler) # [1, 4, 9, 16, 25]
print("Çiftler:", ciftler) # [2, 4]
```

---

## 6. Veri Yapıları (List, Tuple, Dict, Set)

Python'da en yaygın kullanılan 4 temel veri yapısı vardır:

| Veri Yapısı | Sözdizimi | Sıralı mı? (Ordered) | Değiştirilebilir mi? (Mutable) | Tekrar eden eleman (Duplicate) |
| :--- | :--- | :--- | :--- | :--- |
| **List (Liste)** | `[1, 2, 3]` | Evet | Evet | İzin verir |
| **Tuple (Demet)**| `(1, 2, 3)` | Evet | Hayır | İzin verir |
| **Dict (Sözlük)**| `{"k": "v"}`| Evet (Py 3.7+) | Evet (Key benzersiz) | Key tekildir, Value tekrar edebilir |
| **Set (Küme)** | `{1, 2, 3}` | Hayır | Evet | İzin vermez (Benzersizdir) |

---

### A. Listeler (`list`)
Elemanları sıralı tutan ve sonradan değiştirilebilen koleksiyonlardır.

```python
sayilar = [10, 20, 30, 40, 50]

# İndeksleme ve Dilimleme (Slicing)
print(sayilar[0])       # İlk eleman: 10
print(sayilar[-1])      # Son eleman: 50
print(sayilar[1:4])     # 1, 2 ve 3. indeksler: [20, 30, 40]
print(sayilar[::-1])    # Listeyi ters çevirme

# Yaygın Metotlar
sayilar.append(60)      # Sona eleman ekler
sayilar.insert(1, 15)   # 1. indekse 15 ekler
sayilar.pop()           # Son elemanı çıkarır
sayilar.remove(20)      # 20 değerini siler
sayilar.sort()          # Küçükten büyüğe sıralar

# List Comprehension (Kompakt Liste Oluşturma)
cift_kareler = [x**2 for x in range(10) if x % 2 == 0]
print(cift_kareler)     # [0, 4, 16, 36, 64]
```

---

### B. Demetler (`tuple`)
Listelere benzer ancak **değiştirilemezler (immutable)**. Değerlerin sabit kalması gereken durumlarda ve hızlı veri aktarımında kullanılır.

```python
koordinatlar = (41.0082, 28.9784)
# koordinatlar[0] = 40.0  -> HATA verir! (TypeError)

# Tek elemanlı tuple oluştururken virgüle dikkat edilmelidir:
tek_eleman = (5,)  # type: tuple
sayi_grubu = (5)   # type: int

# Tuple Unpacking (Paket Açma)
enlem, boylam = koordinatlar
print(f"Enlem: {enlem}, Boylam: {boylam}")
```

---

### C. Sözlükler (`dict`)
Anahtar-değer (Key-Value) çiftleri ile çalışır. Hızlı arama ve veri eşleştirme için idealdir.

```python
kullanici = {
    "id": 101,
    "isim": "Can",
    "roller": ["admin", "editor"]
}

# Erişme ve Değiştirme
print(kullanici["isim"])                # Can
print(kullanici.get("yas", "Bilinmiyor")) # Anahtar yoksa hata vermez, varsayılan döner

kullanici["yas"] = 30                   # Yeni anahtar-değer ekleme
kullanici["isim"] = "Can Yılmaz"        # Değer güncelleme

# Sözlük üzerinde gezinme
for anahtar, deger in kullanici.items():
    print(f"{anahtar}: {deger}")

# Dict Comprehension
kareler_dict = {x: x**2 for x in range(1, 5)}
print(kareler_dict) # {1: 1, 2: 4, 3: 9, 4: 16}
```

---

### D. Kümeler (`set`)
Sırasız ve indekslenemez koleksiyonlardır. En önemli özelliği **mükerrer (tekrar eden) eleman barındırmamasıdır**.

```python
kume1 = {1, 2, 3, 3, 4}
print(kume1) # {1, 2, 3, 4} (Tekrar eden 3 silindi)

kume2 = {3, 4, 5, 6}

# Küme İşlemleri
print(kume1 | kume2)   # Birleşim (Union): {1, 2, 3, 4, 5, 6}
print(kume1 & kume2)   # Kesişim (Intersection): {3, 4}
print(kume1 - kume2)   # Fark (Difference): {1, 2}
print(kume1 ^ kume2)   # Simetrik Fark: {1, 2, 5, 6}
```

---

## 7. Nesne Yönelimli Programlama (OOP) & Sınıflar

Nesne Yönelimli Programlama (Object-Oriented Programming), kodları gerçek dünyadaki nesneleri modelleyerek daha düzenli, yeniden kullanılabilir ve bakımı kolay hale getirmeyi sağlar.

### Temel Sınıf ve Nesne Tanımı
- `class`: Sınıf tanımlama anahtar kelimesi.
- `__init__`: Nesne oluşturulurken otomatik çalışan yapıcı (constructor) metot.
- `self`: Sınıftan türetilen nesnenin kendisine işaret eden referans.

```python
class Araba:
    # Sınıf Niteliği (Class Attribute - Tüm nesneler için ortak)
    tekerlek_sayisi = 4

    def __init__(self, marka, model, yil):
        # Örnek Nitelikleri (Instance Attributes - Nesneye özel)
        self.marka = marka
        self.model = model
        self.yil = yil
        self.hiz = 0

    def hizlan(self, miktar):
        self.hiz += miktar
        print(f"{self.marka} hızlandı. Güncel hız: {self.hiz} km/s")

    def bilgileri_goster(self):
        return f"{self.yil} {self.marka} {self.model} - Hız: {self.hiz} km/s"

# Nesne oluşturma (Instantiation)
araba1 = Araba("Toyota", "Corolla", 2022)
araba2 = Araba("Volvo", "XC90", 2023)

araba1.hizlan(50)
print(araba1.bilgileri_goster())
```

---

### Kalıtım (Inheritance) & `super()`
Bir sınıfın başka bir sınıfın özelliklerini ve metotlarını devralmasıdır.

```python
class ElektrikliAraba(Araba):
    def __init__(self, marka, model, yil, batarya_kapasitesi):
        # Üst sınıfın (Araba) __init__ metodunu çağırıyoruz
        super().__init__(marka, model, yil)
        self.batarya_kapasitesi = batarya_kapasitesi

    # Metot Ezme (Method Overriding)
    def bilgileri_goster(self):
        temel_bilgi = super().bilgileri_goster()
        return f"{temel_bilgi} [Batarya: {self.batarya_kapasitesi} kWh]"

tesla = ElektrikliAraba("Tesla", "Model 3", 2023, 75)
tesla.hizlan(80)
print(tesla.bilgileri_goster())
```

---

### Kapsülleme (Encapsulation)
Verilere doğrudan erişimi sınırlandırarak güvenliği artırma prensibidir.
- `_degisken` : Korumalı (Protected) - Alt sınıflar erişebilir, dışarıdan erişilmesi önerilmez.
- `__degisken`: Gizli (Private) - Sınıf dışından doğrudan erişilemez (Name Mangling uygulanır).

```python
class BankaHesabi:
    def __init__(self, sahip, bakiye):
        self.sahip = sahip
        self.__bakiye = bakiye  # Private değişken

    def bakiye_goruntule(self):
        return f"Sayın {self.sahip}, bakiyeniz: {self.__bakiye} TL"

    def para_yatir(self, miktar):
        if miktar > 0:
            self.__bakiye += miktar
            print(f"{miktar} TL yatırıldı.")
        else:
            print("Geçersiz miktar!")

hesap = BankaHesabi("Elif", 1500)
hesap.para_yatir(500)
print(hesap.bakiye_goruntule())

# Doğrudan erişim hata verir:
# print(hesap.__bakiye) -> AttributeError!
```

---

### Çok Biçimlilik (Polymorphism)
Farklı sınıfların aynı isimli metoda sahip olabilmesi ve bu metotların nesneye göre farklı davranabilmesidir.

```python
class Kedi:
    def ses_cikar(self):
        return "Miyav!"

class Kopek:
    def ses_cikar(self):
        return "Hav hav!"

hayvanlar = [Kedi(), Kopek()]
for hayvan in hayvanlar:
    print(hayvan.ses_cikar())
```

---

### Özel / Dunder Metotlar (`__str__`, `__len__`, `__repr__`)
Python sınıflarında yerleşik fonksiyonlarla (`str()`, `len()`, `print()`) uyumlu çalışmayı sağlayan özel metotlardır.

```python
class Kitap:
    def __init__(self, baslik, yazar, sayfa_sayisi):
        self.baslik = baslik
        self.yazar = yazar
        self.sayfa_sayisi = sayfa_sayisi

    def __str__(self):
        # print() ve str() çağrıldığında okunabilir çıktı üretir
        return f"'{self.baslik}' - {self.yazar}"

    def __len__(self):
        # len() çağrıldığında sayfa sayısını döner
        return self.sayfa_sayisi

kitap = Kitap("Dönüşüm", "Franz Kafka", 160)
print(kitap)        # 'Dönüşüm' - Franz Kafka
print(len(kitap))   # 160
```

---

## Özet ve En İyi Uygulamalar (Best Practices)
1. **PEP 8 Kurallarına Uyun**: Değişken ve fonksiyon isimlerinde `snake_case`, sınıf isimlerinde `PascalCase` kullanın.
2. **Girintilere Dikkat Edin**: Python'da girinti (indentation) mantıksal blokları belirler; standart olarak 4 boşluk kullanın.
3. **Doğru Veri Yapısını Seçin**:
   - Değerler değişecekse: `list`
   - Değerler sabit kalacaksa: `tuple`
   - Anahtar-değer ilişkisi varsa: `dict`
   - Benzersizlik gerekiyorsa: `set`
4. **Kodlarınızı Fonksiyon ve Sınıflarla Modüler Tutun**: Tekrar eden kodlardan kaçının (DRY - Don't Repeat Yourself prensibi).
