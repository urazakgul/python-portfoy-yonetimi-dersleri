# Python ile Portföy Yönetimi Dersleri

- [Python ile Portföy Yönetimi Dersleri](#python-ile-portföy-yönetimi-dersleri)
- [1. Giriş](#1-giriş)
- [2. Kullanılacak Kütüphaneler ve Sabit Değişkenler](#2-kullanılacak-kütüphaneler-ve-sabit-değişkenler)
- [3. Veri Kaynakları](#3-veri-kaynakları)
  - [3.1. yfinance (Ana Kaynak)](#31-yfinance-ana-kaynak)
  - [3.2. isyatirimhisse (Alternatif)](#32-isyatirimhisse-alternatif)
- [4. Getiri](#4-getiri)
  - [4.1. Getiri Nedir?](#41-getiri-nedir)
  - [4.2. Tek Dönemlik Basit Getiri](#42-tek-dönemlik-basit-getiri)
  - [4.3. Çok Dönemli Basit (Bileşik) Getiri](#43-çok-dönemli-basit-bileşik-getiri)
  - [4.4. Sürekli Bileşik Getiri veya Logaritmik Getiri](#44-sürekli-bileşik-getiri-veya-logaritmik-getiri)
  - [4.5. Reel Getiri](#45-reel-getiri)
  - [4.6. Beklenen Getiri ve Hesaplama Yöntemleri](#46-beklenen-getiri-ve-hesaplama-yöntemleri)
    - [4.6.1. Tarihsel Ortalama](#461-tarihsel-ortalama)
    - [4.6.2. Senaryoya Bağlı Ağırlıklandırılmış Olasılıklar](#462-senaryoya-bağlı-ağırlıklandırılmış-olasılıklar)
    - [4.6.3. Finansal Varlık Fiyatlama Modeli (CAPM), Klasik CAPM](#463-finansal-varlık-fiyatlama-modeli-capm-klasik-capm)
- [5. Risk](#5-risk)
  - [5.1. Risk Nedir?](#51-risk-nedir)
  - [5.2. Volatilite Nedir?](#52-volatilite-nedir)
  - [5.3. Volatilite Ölçüm Yöntemleri](#53-volatilite-ölçüm-yöntemleri)
    - [5.3.1. Varyans ve Standart Sapma](#531-varyans-ve-standart-sapma)
    - [5.3.2. Üstsel Ağırlıklandırılmış Hareketli Ortalama (EWMA)](#532-üstsel-ağırlıklandırılmış-hareketli-ortalama-ewma)
    - [5.3.3. Otoregresif Koşullu Değişen Varyans (GARCH)](#533-otoregresif-koşullu-değişen-varyans-garch)
- [6. Portföy Getirisinin ve Riskinin Ölçülmesi](#6-portföy-getirisinin-ve-riskinin-ölçülmesi)
  - [6.1. Portföy Getirisi](#61-portföy-getirisi)
  - [6.2. Portföy Getirisinin Ölçülmesi](#62-portföy-getirisinin-ölçülmesi)
  - [6.3. Portföy Riski](#63-portföy-riski)
  - [6.4. Portföy Riskinin Ölçülmesi](#64-portföy-riskinin-ölçülmesi)
  - [6.5. Portföyün Çeşitlendirilmesi ve Riskin Düşürülmesi](#65-portföyün-çeşitlendirilmesi-ve-riskin-düşürülmesi)
  - [6.6. Portföyde Hedeflenen Beklenen Getiriye Göre Ağırlıkların Optimize Edilmesi](#66-portföyde-hedeflenen-beklenen-getiriye-göre-ağırlıkların-optimize-edilmesi)
  - [6.7. Portföy Riskinin Ağırlıkların Optimize Edilmesi ile Minimize Edilmesi](#67-portföy-riskinin-ağırlıkların-optimize-edilmesi-ile-minimize-edilmesi)
- [7. Etkin Sınır](#7-etkin-sınır)
  - [7.1. Etkin Sınır Nedir?](#71-etkin-sınır-nedir)
  - [7.2. Etkin Sınır ve En İyi Portföyün Bulunması](#72-etkin-sınır-ve-en-i̇yi-portföyün-bulunması)
- [8. Portföy Performans Metrikleri](#8-portföy-performans-metrikleri)
  - [8.1. Sharpe Oranı](#81-sharpe-oranı)
  - [8.2. Treynor Oranı](#82-treynor-oranı)
- [9. Riske Maruz Değer (VaR)](#9-riske-maruz-değer-var)
  - [9.1. Parametrik](#91-parametrik)
  - [9.2. Tarihsel Simülasyon](#92-tarihsel-simülasyon)
  - [9.3. Monte Carlo](#93-monte-carlo)
- [10. Portföy Optimizasyonu için Python Paketlerinin İncelenmesi](#10-portföy-optimizasyonu-için-python-paketlerinin-i̇ncelenmesi)
  - [10.1. PyPortfolioOpt](#101-pyportfolioopt)
  - [10.2. empyrial](#102-empyrial)

# 1. Giriş

---

***Amaç: Finans ve Portföy Yönetimi alanına Python programlama dili ile katkı sağlamak ve Türkçe kaynak yaratmak.***

***Varsayım: Okuyucu, Python programlama dilini rahatlıkla kullanabilmektedir. Aynı zamanda İstatistik ve portföy yönetimiyle ilgili terimlere ilişkin temel düzeyde bir bilgi birikimine sahiptir.***

***Dikkat: Kendi deneyimlerim ve araştırmalarım doğrultusunda sunulan bilgiler, yalnızca genel bilgilendirme amaçlıdır ve yatırım tavsiyesi olarak yorumlanmamalıdır.***

***Yararlandığım kaynaklar için teşekkür: Finansal Risk Yönetimi; Burak Saltoğlu, Yatırım El Kitabı-Sermaye Pazarları, Menkul Değerlere Yatırım ve Portföy Yönetimi; Mehmet Şükrü Tekbaş, Finansal Ekonometri; Nilgün Çil Yavuz. Ayrıca, piyasanın üstünde bir kaynağa sahip şirketim RiskTürk'e ve bu kaynakların yaratılmasında ciddi payları olan Product Manager'ımız S.K. ve Manager'ımız Göktay Öncel'e çok teşekkür ederim.***

# 2. Kullanılacak Kütüphaneler ve Sabit Değişkenler

---

Derslerde, aşağıdaki kütüphaneler kullanılacaktır.

```python
import yfinance as yf
from isyatirimhisse import veri_cek # opsiyonel
import pandas as pd
import numpy as np
import statsmodels.api as sm
from arch import arch_model
from scipy.optimize import minimize
from scipy.stats import norm
from pypfopt import EfficientFrontier, risk_models, expected_returns, plotting
from pypfopt.discrete_allocation import DiscreteAllocation, get_latest_prices
from empyrial import empyrial, Engine, get_report
from tabulate import tabulate # opsiyonel
import matplotlib.pyplot as plt
plt.style.use('fivethirtyeight') # opsiyonel
```

Derslerde, iş günü 250 ve risksiz faiz oranı 0.1 (%10) varsayılacaktır.

```python
is_gunu = 250 # İş günü 252 olarak da girilebiliyor
risksiz_faiz_orani = 0.1
```

Hata almamak için yukarıdaki kütüphaneleri çalıştırmanızı ve sabit değişkenleri tanımlamanızı rica ederim.

# 3. Veri Kaynakları

---

## 3.1. yfinance (Ana Kaynak)

`yfinance`, Ran Aroussi tarafından geliştirilen açık kaynak bir Python kütüphanesidir ve Yahoo Finance üzerinde bulunan finansal verilere erişmek için kullanılmaktadır.

Derslerde ana veri kaynağı olarak `yfinance` kütüphanesini kullanacağız. Bu nedenle, nihai fonksiyonu oluşturma aşamalarını göreceğiz ki pakete de hakim olalım.

`THYAO.IS` hisse senedine ait günlük verileri `yfinance` kütüphanesi ile çekelim ve veri çerçevesine aktaralım.

```python
sembol = 'THYAO.IS'
baslangic_tarih = '2023-01-02'
bitis_tarih = '2023-07-29'
tarihsel = yf.download(tickers=sembol, start=baslangic_tarih, end=bitis_tarih)
veriler_df = pd.DataFrame(tarihsel).reset_index()
```

![](/imgs/yfinance_veriler_1.PNG)

`THYAO.IS` ve `GARAN.IS` hisse senetlerine ait günlük verileri `yfinance` kütüphanesi ile çekelim ve veri çerçevesine aktaralım.

```python
semboller = ['THYAO.IS', 'GARAN.IS']
baslangic_tarih = '2023-01-02'
bitis_tarih = '2023-07-29'

veriler_df = pd.DataFrame()
for sembol in semboller:
    tarihsel = yf.download(tickers=sembol, start=baslangic_tarih, end=bitis_tarih)
    veriler_df_alt = pd.DataFrame(tarihsel).reset_index()
    veriler_df_alt['Sembol'] = sembol.replace('.IS', '')
    veriler_df = pd.concat([veriler_df,veriler_df_alt])
```

![](/imgs/yfinance_veriler_2.PNG)

`THYAO.IS` ve `GARAN.IS` hisse senetlerine ait günlük verileri `yfinance` kütüphanesi ile çekelim ve `Date` ve `Close` sütunlarını alıp bir veri çerçevesine semboller yan yana olacak şekilde ekleyelim.

```python
semboller = ['THYAO.IS', 'GARAN.IS']
baslangic_tarih = '2023-01-02'
bitis_tarih = '2023-07-29'

liste = []
for sembol in semboller:
    tarihsel = yf.download(tickers=sembol, start=baslangic_tarih, end=bitis_tarih)
    veriler_df_alt = pd.DataFrame(tarihsel).reset_index()
    veriler_df_alt = veriler_df_alt[['Date', 'Close']].rename(columns={'Close': f'{sembol.replace(".IS", "")}'})
    liste.append(veriler_df_alt)

veriler_df = liste[0]
for i in range(1, len(liste)):
    veriler_df = pd.merge(veriler_df, liste[i], on='Date', how='outer')
```

![](/imgs/yfinance_veriler_3.PNG)

Ders boyunca veri çekeceğiz. Her defasında yukarıdaki kodları yazmak yorucu olacaktır. Süreci kolaylaştırmak adına bir fonksiyon yazabiliriz. Fonksiyonun ismine `yfinance_veri_cek()` diyelim.

```python
def yfinance_veri_cek(sembol, baslangic_tarih, bitis_tarih, frekans):
    liste = []

    for s in sembol:
        tarihsel = yf.download(
            tickers=s,
            start=baslangic_tarih,
            end=bitis_tarih,
            interval=frekans
        )

        veriler_df_alt = pd.DataFrame(tarihsel).reset_index()
        veriler_df_alt = veriler_df_alt[['Date','Adj Close']].rename(columns={'Date':'Tarih','Adj Close':f'{s.replace(".IS","")}'})
        liste.append(veriler_df_alt)

    veriler_df = liste[0]
    for i in range(1,len(liste)):
        veriler_df = pd.merge(veriler_df, liste[i], on='Tarih', how='outer')

    return veriler_df
```

`yfinance_veri_cek()` fonksiyonunu kullanarak `THYAO.IS` ve `GARAN.IS` hisse senetlerine ait aylık verileri çekelim.

```python
semboller = ['THYAO.IS', 'GARAN.IS']
baslangic_tarih = '2023-01-01'
bitis_tarih = '2023-08-01'
frekans = '1mo'

"""

Bazı frekans bilgileri:
    1h: 1 saatlik,
    1d: 1 günlük,
    1wk: 1 haftalık,
    1mo: 1 aylık

"""

veriler_df = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
```

![](/imgs/yfinance_veriler_4.PNG)

`yfinance` kütüphanesi ile borsa endekslerine ait verileri de çekip kullanacağız fakat bilindiği üzere 2020 yılında endekslerden iki sıfır atıldı. `yfinance` verilerinde ise herhangi bir düzeltme yapılmamış. Sonrasında bir düzeltme yapılırsa bu kısmı dikkate almayabilirsiniz. Tabi nihai fonksiyonun da güncellenmesi gerekir.

```python
sembol = ['XU100.IS']
baslangic_tarih = '2020-01-02'
bitis_tarih = '2021-01-01'
frekans = '1d'

veriler_df = yfinance_veri_cek(
    sembol = sembol,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)

plt.plot(
    'Tarih',
    'XU100',
    data=veriler_df,
    color='red'
)
plt.title('BIST 100 Hatalı Veriler')
plt.show()
```

![](/imgs/xu100_hatali.png)

Aşağıdaki fonksiyonu, endeks verileri söz konusu olduğu zaman düzeltme amaçlı kullanacağız.

```python
def endeks_basamak_kontrol(df_duzeltilecek):
    tarih = '2020-07-27'

    problem_df = df_duzeltilecek[df_duzeltilecek['Tarih'] < tarih]
    normal_df = df_duzeltilecek[df_duzeltilecek['Tarih'] >= tarih]

    xu_sutunlar = [xu for xu in problem_df.columns if xu.startswith('XU')]

    for xu_sutun in xu_sutunlar:
        for index, value in enumerate(problem_df[xu_sutun]):
            problem_df.at[index, xu_sutun] = value / 100

    veriler_df = pd.concat([problem_df, normal_df], ignore_index=True)

    return veriler_df
```

Test edelim.

```python
duzeltilmis_df = endeks_basamak_kontrol(df_duzeltilecek=veriler_df)

plt.plot(
    'Tarih',
    'XU100',
    data=duzeltilmis_df,
    color='red'
)
plt.title('BIST 100 Hatasız Veriler')
plt.show()
```

![](/imgs/xu100_hatasiz.png)

Fonksiyonları ayrı ayrı çalıştırmamak için `yfinance_veri_cek()` ve `endeks_basamak_kontrol()` fonksiyonlarını `yfinance_veri_cek()` çatısında birleştirebiliriz.

```python
def yfinance_veri_cek(sembol, baslangic_tarih, bitis_tarih, frekans):
    liste = []

    for s in sembol:
        tarihsel = yf.download(
            tickers=s,
            start=baslangic_tarih,
            end=bitis_tarih,
            interval=frekans
        )

        veriler_df_alt = pd.DataFrame(tarihsel).reset_index()
        veriler_df_alt = veriler_df_alt[['Date','Adj Close']].rename(columns={'Date':'Tarih','Adj Close':f'{s.replace(".IS","")}'})
        liste.append(veriler_df_alt)

    veriler_df = liste[0]
    for i in range(1,len(liste)):
        veriler_df = pd.merge(veriler_df, liste[i], on='Tarih', how='outer')

    tarih = '2020-07-27'
    df_problem = veriler_df[veriler_df['Tarih'] < tarih]
    df_normal = veriler_df[veriler_df['Tarih'] >= tarih]

    xu_sutunlar = [xu for xu in df_problem.columns if xu.startswith('XU')]

    for xu_sutun in xu_sutunlar:
        for index, value in enumerate(df_problem[xu_sutun]):
            df_problem.at[index, xu_sutun] = value / 100

    veriler_df = pd.concat([df_problem, df_normal], ignore_index=True)

    return veriler_df
```

Test edelim.

```python
semboller = ['XU100.IS','XU030.IS']
baslangic_tarih = '2020-01-02'
bitis_tarih = '2023-07-29'
frekans = '1d'

veriler_df = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
veriler_df = veriler_df.dropna()

plt.plot(
    'Tarih',
    'XU100',
    data=veriler_df,
    color='black'
)
plt.plot(
    'Tarih',
    'XU030',
    data=veriler_df,
    color='blue'
)
plt.title('Endekslerin (BIST 100 ve BIST 30) Günlük Veri Kontrolü')
plt.show()
```

![](/imgs/xu100_xu030_hatasiz_gunluk.png)

Yukarıdaki fonksiyon günlük frekansta çalışmaktadır. Aylık frekans için fonksiyona son bir şekil verebiliriz. Diğer frekansları okuyucuya bırakıyorum. Derslerde, günlük ve aylık frekansları kullanacağız.

```python
def yfinance_veri_cek(sembol, baslangic_tarih, bitis_tarih, frekans):
    liste = []

    for s in sembol:
        tarihsel = yf.download(
            tickers=s,
            start=baslangic_tarih,
            end=bitis_tarih,
            interval=frekans
        )

        veriler_df_alt = pd.DataFrame(tarihsel).reset_index()
        veriler_df_alt = veriler_df_alt[['Date','Adj Close']].rename(columns={'Date':'Tarih','Adj Close':f'{s.replace(".IS","")}'})
        liste.append(veriler_df_alt)

    veriler_df = liste[0]
    for i in range(1,len(liste)):
        veriler_df = pd.merge(veriler_df, liste[i], on='Tarih', how='outer')

    if frekans == '1d':
        tarih = '2020-07-27'
        df_problem = veriler_df[veriler_df['Tarih'] < tarih]
        df_normal = veriler_df[veriler_df['Tarih'] >= tarih]

        xu_sutunlar = [xu for xu in df_problem.columns if xu.startswith('XU')]

        for xu_sutun in xu_sutunlar:
            for index, value in enumerate(df_problem[xu_sutun]):
                df_problem.at[index, xu_sutun] = value / 100

        veriler_df = pd.concat([df_problem, df_normal], ignore_index=True)

    elif frekans == '1mo':
        tarih = '2020-07-01'
        df_problem = veriler_df[veriler_df['Tarih'] < tarih]
        df_normal = veriler_df[veriler_df['Tarih'] >= tarih]

        xu_sutunlar = [xu for xu in df_problem.columns if xu.startswith('XU')]

        for xu_sutun in xu_sutunlar:
            for index, value in enumerate(df_problem[xu_sutun]):
                df_problem.at[index, xu_sutun] = value / 100

        veriler_df = pd.concat([df_problem, df_normal], ignore_index=True)

    return veriler_df
```

Test edelim.

```python
semboller = ['XU100.IS','XU030.IS']
baslangic_tarih = '2020-01-01'
bitis_tarih = '2023-08-01'
frekans = '1mo'

df = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
df = df.dropna()

plt.plot(
    'Tarih',
    'XU100',
    data=df,
    color='black'
)
plt.plot(
    'Tarih',
    'XU030',
    data=df,
    color='blue'
)
plt.title('Endekslerin (BIST 100 ve BIST 30) Aylık Veri Kontrolü')
plt.show()
```

![](/imgs/xu100_xu030_hatasiz_aylik.png)

Derslerde sürekli olarak getiri hesaplayacağız. Bunu da tekrar tekrar hesaplamamak için fonksiyona ekleyelim.

```python
def yfinance_veri_cek(sembol, baslangic_tarih, bitis_tarih, frekans, getiri=True, log_getiri=True):
    liste = []

    for s in sembol:
        tarihsel = yf.download(
            tickers=s,
            start=baslangic_tarih,
            end=bitis_tarih,
            interval=frekans
        )

        veriler_df_alt = pd.DataFrame(tarihsel).reset_index()
        veriler_df_alt = veriler_df_alt[['Date','Adj Close']].rename(columns={'Date':'Tarih','Adj Close':f'{s.replace(".IS","")}'})
        liste.append(veriler_df_alt)

    veriler_df = liste[0]
    for i in range(1,len(liste)):
        veriler_df = pd.merge(veriler_df, liste[i], on='Tarih', how='outer')

    if frekans == '1d':
        tarih = '2020-07-27'
        df_problem = veriler_df[veriler_df['Tarih'] < tarih]
        df_normal = veriler_df[veriler_df['Tarih'] >= tarih]

        xu_sutunlar = [xu for xu in df_problem.columns if xu.startswith('XU')]

        for xu_sutun in xu_sutunlar:
            for index, value in enumerate(df_problem[xu_sutun]):
                df_problem.at[index, xu_sutun] = value / 100

        veriler_df = pd.concat([df_problem, df_normal], ignore_index=True)

    elif frekans == '1mo':
        tarih = '2020-07-01'
        df_problem = veriler_df[veriler_df['Tarih'] < tarih]
        df_normal = veriler_df[veriler_df['Tarih'] >= tarih]

        xu_sutunlar = [xu for xu in df_problem.columns if xu.startswith('XU')]

        for xu_sutun in xu_sutunlar:
            for index, value in enumerate(df_problem[xu_sutun]):
                df_problem.at[index, xu_sutun] = value / 100

        veriler_df = pd.concat([df_problem, df_normal], ignore_index=True)

    veriler_df = veriler_df.set_index('Tarih')

    if getiri and log_getiri:
        veriler_df = veriler_df.apply(lambda x: np.log(x / x.shift(1)))
    elif getiri and not log_getiri:
        veriler_df = veriler_df.apply(lambda x: x / x.shift(1) - 1)
    elif not getiri:
        veriler_df

    veriler_df = veriler_df.reset_index()
    veriler_df = veriler_df.dropna()
    veriler_df = veriler_df.reset_index(drop=True)

    return veriler_df
```

Test edelim.

```python
# Getiri hesaplasın ve logaritmik getiri olsun

semboller = ['XU100.IS', 'THYAO.IS']
baslangic_tarih = '2018-06-01'
bitis_tarih = '2023-08-01'
frekans = '1mo'

veriler_df = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
```

![](/imgs/yfinance_log_getiri_test.PNG)

```python
# Getiri hesaplasın ve basit getiri olsun

semboller = ['XU100.IS', 'THYAO.IS']
baslangic_tarih = '2018-06-01'
bitis_tarih = '2023-08-01'
frekans = '1mo'
log_getiri = False

veriler_df = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans,
    log_getiri = log_getiri
)
```

![](/imgs/yfinance_basit_getiri_test.PNG)

```python
# Getiri hesaplamasın

semboller = ['XU100.IS', 'THYAO.IS']
baslangic_tarih = '2018-06-01'
bitis_tarih = '2023-08-01'
frekans = '1mo'
getiri = False

veriler_df = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans,
    getiri = getiri
)
```

![](/imgs/yfinance_fiyat_test.PNG)

## 3.2. isyatirimhisse (Alternatif)

Alternatif bir veri kaynağı olan `İş Yatırım`'ın web sitesinden verileri almak için `isyatirimhisse` kütüphanesi kullanılabilir. Elde edilecek çıktılar ile `yfinance_veri_cek()` fonksiyonuna ait çıktılar aynı olacaktır.

* PyPI: https://pypi.org/project/isyatirimhisse/
* GitHub Repo: https://github.com/urazakgul/isyatirimhisse

# 4. Getiri

---

## 4.1. Getiri Nedir?

Getiri, bir finansal varlığın zaman içinde elde ettiği kazanç veya geliri ifade eder ve genellikle yüzde olarak ifade edilir.

## 4.2. Tek Dönemlik Basit Getiri

Bir varlığın $t$ dönemindeki fiyatı $P_t$ olsun. Tek dönemlik basit getiri nispi fiyat değişmeleri temel alınarak hesaplanır.

$r_t = \frac{P_t - P_{t-1}}{P_{t-1}}$

Yukarıdaki getiri hesaplamasında sadece sermaye kazancı (değer artışı) dikkate alınmış olup hisse senetleri için temettü ödemesi (kar payı) dikkate alınmamıştır.

Temettü ödemesi dahil edilmiş formül aşağıdaki gibi olacaktır.

$r_t = \frac{P_t - P_{t-1}}{P_{t-1}} + \frac{D_t}{P_{t-1}}$

Yukarıdaki formülde, sol taraf sermaye kazancının getirisini, sağ taraf ise temettü getirisini temsil etmektedir.

Örneğin, bir hisse senedini Haziran 2023'te 100 ₺'den aldığımızı ve aynı hisse senedini Temmuz 2023'te 120 ₺'den sattığımızı varsayalım. İlgili dönemde de herhangi bir temettü ödemesi olmasın.

1 aylık basit getiri, $r_t = \frac{120 - 100}{100} = \frac{20}{100} = 0.2$ veya %20'dir.

Örneğimizden devam edelim ve aynı dönemde 5 ₺'lik bir temettü ödemesinin yapıldığını varsayalım. Bu durumda ise getiri, $r_t = \frac{120 - 100}{100} + \frac{5}{100} = 0.2 + 0.05 = 0.25$ veya %25'tir. Burada, %20 sermaye kazancı getirisi, %5 ise temettü getirisidir.

## 4.3. Çok Dönemli Basit (Bileşik) Getiri

Finansal varlığın, $t-k \ (k > 1)$ ile $t$ tarihleri arasında k dönem elde tutulduğu durumlarda k sayıda tek dönemlik basit getiri sağlanır. Çok dönemli basit getiri veya bileşik getiri aşağıdaki gibi formülize edilebilir.

$r_t[k] = \frac{P_t - P_{t-k}}{P_{t-k}}$ veya,

$r_t[k] = (1 + r_t)(1 + r_{t-1})...(1 + r_{t-k}) - 1$

Örneğin, bir hisse senedini Mayıs 2023'te 80 ₺'den aldığımızı ve aynı hisse senedini Temmuz 2023'te 120 ₺'den sattığımızı varsayalım. Haziran 2023 fiyatı 100 ₺ idi.

2 aylık basit getiriyi iki yoldan heaplayabiliriz.

Birincisi, basit getiri şeklinde hesaplayabiliriz.

$r_t[2] = \frac{120 - 80}{80} = 0.5$ veya %50'dir

İkincisi, bileşik getiriyi kullanabiliriz.

Mayıs ayından Haziran ayına: $\frac{100 - 80}{80} = 0.25$

Haziran ayından Temmuz ayına: $\frac{120 - 100}{100} = 0.20$

$r_t[2] = (1 + 0.25) x (1 + 0.20) - 1 = 1.5 - 1 = 0.5$ veya %50'dir.

## 4.4. Sürekli Bileşik Getiri veya Logaritmik Getiri

Logaritmik getiri, getirinin sürekli bileşik getiri olarak kabul edilmesini sağlar. Bu nedenle, farklı dönemlerin getirileri toplandığında daha doğru sonuçlar elde edilir.

$r_t = ln(\frac{P_t}{P_{t-1}}) = ln(P_t) - ln(P_{t-1})$

Temettü ödemesi dikkate alındığında formül aşağıdaki gibi olacaktır.

$r_t = ln(\frac{P_t + D_t}{P_{t-1}}) = ln(P_t + D_t) - ln(P_{t-1})$

Örneğin, bir hisse senedini Haziran 2023'te 100 ₺'den aldığımızı ve aynı hisse senedini Temmuz 2023'te 120 ₺'den sattığımızı varsayalım. İlgili dönemde de herhangi bir temettü ödemesi olmasın.

1 aylık logaritmik getiri, $r_t = ln(\frac{120}{100}) = ln(120) - ln(100) = 0.18$ veya %18'dir.

Örneğimizden devam edelim ve aynı dönemde 5 ₺'lik bir temettü ödemesinin yapıldığını varsayalım. Bu durumda ise getiri, $r_t = ln(\frac{120 + 5}{100}) = ln(120 + 5) - ln(100) = 0.22$ veya %22'dir.

`THYAO.IS` hisse senedinin Aralık/2021 ile Aralık/2022 tarihleri arasındaki aylık fiyatlarından logaritmik getiriyi hesaplayalım.

```python
sembol = ['THYAO.IS']
baslangic_tarih = '2021-12-01'
bitis_tarih = '2023-01-01'
frekans = '1mo'

veriler_df = yfinance_veri_cek(
    sembol = sembol,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
```

![](/imgs/log_getiri.PNG)

`THYAO.IS` hisse senedinin 2022 yılı aylık verilerinden yıllık sürekli bileşik getirisini `THYAO` sütununu toplayarak hesaplayabiliriz. Aynı zamanda, benzer sonuca getirilerin ortalamasını aylık frekansta veriler olduğu için 12 ile çarptığımızda da ulaşabiliriz.

```python
yillik_surekli_bilesik_getiri_toplam = (veriler_df['THYAO'].sum()) * 100
yillik_surekli_bilesik_getiri_ortalama_12 = (veriler_df['THYAO'].mean() * 12) * 100
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['THYAO',yillik_surekli_bilesik_getiri_toplam,yillik_surekli_bilesik_getiri_ortalama_12]],
    headers=['Yıllık Sürekli Bileşik Getiri (Toplam), %','Yıllık Sürekli Bileşik Getiri (Çarpım, 12), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/yillik_surekli_bilesik_getiri.PNG)

## 4.5. Reel Getiri

Nominal getiri, bir finansal varlığın kazandırdığı mutlak miktarı gösterirken, reel getiri, enflasyonun yarattığı satın alma gücü kaybını hesaba katarak gerçek getiriyi ölçer.

$r_t^{reel} = r_t - \pi_t$

Yukarıda, logaritmik getiriden enflasyon oranını çıkarmış oluyoruz.

Daha önce hesapladığımız `THYAO.IS` hisse senedine ait aylık logaritmik getirileri enflasyondan arındıralım.

```python
# Ocak/2022 - Aralık/2022 Aylık Enflasyon Verileri
enflasyon = pd.Series([11.1,4.81,5.46,7.25,2.98,4.95,2.37,1.46,3.08,3.54,2.88,1.18]) / 100

veriler_df = pd.concat([veriler_df, enflasyon.to_frame(name='Enflasyon')], axis=1)
```

`THYAO` sütunu değerlerinden `Enflasyon` sütunu değerlerini çıkardığımızda reel getirilere ulaşacağız.

```python
veriler_df['ReelGetiri'] = veriler_df['THYAO'] - veriler_df['Enflasyon']
```

![](/imgs/reel_log_getiri.PNG)

```python
yillik_surekli_bilesik_reel_getiri = (veriler_df['ReelGetiri'].sum()) * 100
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['THYAO',yillik_surekli_bilesik_getiri_toplam,yillik_surekli_bilesik_reel_getiri]],
    headers=['Yıllık Sürekli Bileşik Getiri, %','Yıllık Sürekli Bileşik Reel Getiri, %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/yillik_surekli_bilesik_getiri_nominal_reel.PNG)

Yıllık sürekli bileşik getiri enflasyondan arındırılınca %144.1'e düşmüştür.

Nominal getiri ile reel getiri arasındaki farkı görsel olarak da inceleyebiliriz.

```python
plt.plot(
    'Tarih',
    'THYAO',
    data=veriler_df,
    color='blue',
    label='Nominal Getiri'
)
plt.plot(
    'Tarih',
    'ReelGetiri',
    data=veriler_df,
    color='red',
    label='Reel Getiri'
)
plt.ylabel('Getiri (%)', fontsize='12')
plt.title('THYAO Hisse Senedi Aylık Getirileri (Ocak/2022 - Aralık/2022)', fontsize='14')
plt.legend(fontsize='xx-small', loc='lower right')
plt.show()
```

![](/imgs/nominal_reel_getiri.png)

## 4.6. Beklenen Getiri ve Hesaplama Yöntemleri

Beklenen Getiri, geçmiş getirilerden yola çıkarak hesaplanan ve gelecekte beklenen getiridir.

Çalışacağımız verileri alalım ve beklenen getiri hesaplama yöntemlerine bakalım.

```python
sembol = ['THYAO.IS']
baslangic_tarih = '2018-08-16'
bitis_tarih = '2023-07-29'
frekans = '1d'

veriler_df = yfinance_veri_cek(
    sembol = sembol,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
```

```python
plt.hist(
    veriler_df['THYAO'] * 100,
    color='red',
    bins='auto'
)
plt.title('THYAO Getirileri (16/08/2018 - 28/07/2023)')
plt.yticks([])
plt.axvline(x=0, color='black', linestyle='--')
plt.show()
```

![](/imgs/beklenen_getiri.png)

### 4.6.1. Tarihsel Ortalama

Bu yöntemde, geçmiş getirilerin ortalamasını alıyoruz.

$E[r_j] = \frac{1}{n} \sum_{t=1}^{n}r_j$

```python
beklenen_getiri_ortalama_gunluk = (veriler_df['THYAO'].mean()) * 100
```

Yukarıda hesaplanan getiri günlüktür.

Bunu, iki yöntemden biri ile yıllıklandırabiliriz.

Birincisi, günlük beklenen getiriyi iş günü ile çarpmak olabilir.

```python
beklenen_getiri_ortalama_yillik_1 = beklenen_getiri_ortalama_gunluk * is_gunu
```

İkincisi, aşağıdaki formülü kullanmak olabilir.

$E[r_{THYAO}] = (1 + 0.22\%)^{250} - 1$

```python
beklenen_getiri_ortalama_yillik_2 = ((1 + beklenen_getiri_ortalama_gunluk/100)**is_gunu - 1) * 100
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['THYAO',beklenen_getiri_ortalama_gunluk,beklenen_getiri_ortalama_yillik_1,beklenen_getiri_ortalama_yillik_2]],
    headers=['Beklenen Getiri (Günlük), %','Beklenen Getiri (Yıllık), %','Beklenen Getiri (Yıllık), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/beklenen_getiri_tarihsel_ortalama.PNG)

### 4.6.2. Senaryoya Bağlı Ağırlıklandırılmış Olasılıklar

Bu yöntem, belirli bir durumun gerçekleşmesi olasılığına göre farklı senaryoların ağırlıklarını dikkate alarak beklenen değeri tahmin etmeyi sağlar.

$E[r_j] = \sum_{i=1}^{s}r_{ji}p_i$

Aşağıda, `THYAO.IS` hisse senedi için 12 analistin 1 yıllık fiyat tahminleri bulunmaktadır.

![](/imgs/senaryo_ongoru.PNG)

İki tane durum belirleyelim: Yükselecek ve Düşecek. Bu olasılıklar ise sırasıyla %55 ve %45 olsun. Bu senaryoda beklenen getiri, $E[r_{THYAO}] = (0.55 x 0.4879) + (0.35 x (-0.4659)) = 0.105$ veya %10.5'tir.

```python
durum_dusecek_olasilik = 0.35
getiri_dusecek = -0.4659
durum_yukselecek_olasilik = 0.55
getiri_yukselecek = 0.4879
cari_fiyat = 198.2

beklenen_getiri = (durum_dusecek_olasilik * getiri_dusecek) + (durum_yukselecek_olasilik * getiri_yukselecek)
beklenen_fiyat = cari_fiyat * (1 + beklenen_getiri)
```

Beklenen getiri ve beklenen fiyat aşağıdaki gibi olacaktır.

```python
print(tabulate(
    [[
        'THYAO',
        durum_dusecek_olasilik*100,
        getiri_dusecek*100,
        durum_yukselecek_olasilik*100,
        getiri_yukselecek*100,
        beklenen_getiri*100,
        cari_fiyat,
        beklenen_fiyat
    ]],
    headers=[
        'Düşme\nOlasılığı, %',
        'Beklenen\nDüşme, %',
        'Yükselme\nOlasılığı, %',
        'Beklenen\nYükselme, %',
        'Beklenen\nGetiri, %',
        'Cari\nFiyat, TL',
        'Beklenen\nFiyat, TL'
    ],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/beklenen_getiri_senaryo.PNG)

### 4.6.3. Finansal Varlık Fiyatlama Modeli (CAPM), Klasik CAPM

CAPM (Capital Asset Pricing Model), finansal varlıkların beklenen getirisini hesaplamak ve fiyatlandırmak için kullanılan bir modeldir. CAPM, varlıkların getirisi ile sistematik risk (piyasa riski) arasındaki ilişkiyi tanımlar.

$E[r_j] = r_f + \beta_j(E[r_m] - r_f)$

$E[r_j]$: Varlık j'nin beklenen getirisi.

$r_f$: Risksiz faiz oranı.

$\beta_j$: Varlık j'nin beta katsayısı. Bu, bir varlığın sistemik riskini ölçen bir katsayıdır. Beta değeri, varlığın piyasa getirilerine olan hassasiyetini gösterir. Beta değeri 1'den büyük ise varlık piyasadan daha fazla hareket eder (daha yüksek risk). Beta değeri 1'den küçük ise varlık piyasadan daha az hareket eder (daha düşük risk).

$E[r_m]$: Piyasa getirisi. Bu, piyasa endeksi veya genel olarak piyasanın beklenen getirisini temsil eder. Piyasa endeksi genellikle S&P 500 veya BIST 100 gibi endekslerden seçilir.

Uygulamada, hisse senedi `THYAO.IS`, endeks `XU100.IS` olacaktır.

```python
sembol = ['XU100.IS','THYAO.IS']
baslangic_tarih = '2018-07-17'
bitis_tarih = '2023-07-29'
frekans = '1d'

veriler_df = yfinance_veri_cek(
    sembol = sembol,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
```

```python
zaman = range(len(veriler_df))
plt.scatter(
    'XU100',
    'THYAO',
    data=veriler_df,
    c=zaman,
    cmap='Reds'
)
plt.xlabel('BIST 100')
plt.ylabel('THYAO')
plt.title('BIST 100 ve THYAO Getirileri (17/07/2018 - 28/07/2023)')
plt.show()
```

![](/imgs/getiriler_capm_grafik.png)

Beklenen getiri ve beta değerini hesaplayacak fonksiyonları yazalım.

```python
def beklenen_getiri_hesapla(df, hisse_senedi, endeks, risksiz_faiz_orani, is_gunu):
    piyasa_getirisi = df[endeks].mean() * is_gunu
    beta = beta_hesapla(df, hisse_senedi, endeks)
    beklenen_getiri = risksiz_faiz_orani + beta * (piyasa_getirisi - risksiz_faiz_orani)
    beklenen_getiri *= 100
    return beklenen_getiri

def beta_hesapla(df, hisse_senedi, endeks):
    X = df[endeks]
    X = sm.add_constant(X)
    y = df[hisse_senedi]

    model = sm.OLS(y, X).fit()
    beta = model.params[endeks]

    return beta
```

Beklenen getiriyi hesaplayalım.

```python
beklenen_getiri = beklenen_getiri_hesapla(
    df = veriler_df,
    hisse_senedi = 'THYAO',
    endeks = 'XU100',
    risksiz_faiz_orani = risksiz_faiz_orani,
    is_gunu = is_gunu
)
```

Piyasa getirisi, XU100'ün ortalaması olarak alındığı için buradan  ~0.002 gelecektir. Yıllıklandırılmış değeri ise ~0.41 olacaktır. Bunun yanında beta ~1.2 hesaplanacaktır. Yani, beta değeri 1.2 olan bir hisse senedinin (örneğimizde THYAO), piyasa endeksi olan XU100'deki %1'lik bir artışta, %1.2 oranında artması beklenir. Aynı şekilde, piyasa endeksi düşerse, hisse senedi de daha fazla düşebilir. Değerleri yerine koyarsak, $0.1 + 1.2 x (0.41 - 0.1)$, beklenen getiriyi %46.2 hesaplıyoruz. Yaklaşık değerler alındığı için kod tam değeri verecektir.

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['THYAO',beklenen_getiri]],
    headers=['Beklenen Getiri (Yıllık), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/beklenen_getiri_capm.PNG)

# 5. Risk

---

## 5.1. Risk Nedir?

Risk, belirsizlikle ilişkili olumsuz sonuçların ortaya çıkma olasılığıdır ve bir yatırımın veya finansal bir enstrümanın beklenen getirisine veya değerine ilişkin belirsizlikleri olarak ifade edilebilir. Riski, piyasa riski ve şirkete özgü risk toplamı şeklinde yazabiliriz. Piyasa riski, finansal piyasalardaki genel dalgalanmalardan kaynaklanan riski ifade eder. Bu risk genellikle tüm piyasaları ve şirketleri etkileyebilir. Piyasa riski, makroekonomik faktörler, siyasi olaylar, faiz oranlarındaki değişiklikler, döviz kurlarındaki dalgalanmalar, emtia fiyatlarındaki değişimler gibi geniş çaplı etkenlerden kaynaklanır. Örnek bir piyasa riski senaryosu, genel ekonomik durumun kötüye gitmesi ve tüketici harcamalarının düşmesiyle ortaya çıkabilir. Bu durumda, birçok şirketin satışları azalabilir, karlılıkları etkilenebilir ve hisse senetlerinin değeri düşebilir. Bu tür bir piyasa riski, genellikle tüm endüstrilerde faaliyet gösteren şirketleri etkiler. Şirkete özgü risk ise belirli bir şirketin faaliyetleri, yönetimi, finansal durumu veya sektöründeki faktörler gibi şirketle ilgili özel faktörlerden kaynaklanan riski ifade eder. Bu risk, yalnızca belirli bir şirketi etkiler ve genellikle diğer şirketlerden farklıdır. Örnek olarak, bir şirketin ürününün talebinde ani bir düşüş yaşaması veya pazar payını kaybetmesi, şirkete özgü riske örnek olabilir. Ayrıca, bir şirketin yönetim ekibindeki hatalı kararlar veya operasyonel sorunlar da şirkete özgü riske katkıda bulunabilir. Bu tür bir risk, genellikle belirli bir sektörde veya şirkette faaliyet gösteren yatırımcıları etkiler, diğer sektörler veya şirketler üzerinde aynı etkiyi doğurmaz.

## 5.2. Volatilite Nedir?

Risk ve volatilite arasında yakın bir ilişki vardır, çünkü volatilite, finansal piyasalardaki fiyat dalgalanmalarının ölçüsüdür ve riskin bir göstergesidir. Bir finansal varlık veya piyasa ne kadar hızlı ve büyük fiyat değişiklikleri gösterirse, o kadar yüksek bir volatilite seviyesine sahip olduğu söylenir.

Volatilite, gerçekleşen (tarihi) ve tahmini olmak üzere iki türe ayrılabilir.

`THYAO.IS` hisse senedinin logaritmik getirilerinden aşağıdaki yöntemleri kullanarak volatilite hesaplayalım.

```python
sembol = ['THYAO.IS']
baslangic_tarih = '2018-08-16'
bitis_tarih = '2023-07-29'
frekans = '1d'

veriler_df = yfinance_veri_cek(
    sembol = sembol,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
```

## 5.3. Volatilite Ölçüm Yöntemleri

### 5.3.1. Varyans ve Standart Sapma

Varyans, bir veri kümesindeki değerlerin ortalama değerinden ne kadar uzaklaştığını ölçen bir istatistiksel ölçümdür. Varyans, her veri noktasının ortalama değerden farkını alıp bu farkların karelerinin ortalamasını hesaplayarak elde edilir. Varyans, veri noktalarının dağılımının ne kadar geniş olduğunu gösterir.

$\sigma_j^2 = \frac{1}{n-1}\sum_{t=1}^{n}(r_j - E[r_j])^2$

Varyans, aşağıdaki gibi hesaplanabilir.

```python
varyans = np.var(veriler_df['THYAO'], ddof=1)
```

Standart sapma varyansın kareköküdür. Standart sapma, veri noktalarının ortalama değerden ne kadar uzaklaştığını ölçerken, birimlerin orijinal veri birimleriyle uyumlu olmasını sağlar. Standart sapma, varyansın karekökü olarak hesaplanır ve genellikle varyansın yanında kullanılır.

$\sigma_j = \sqrt{\frac{1}{n-1}\sum_{t=1}^{n}(r_j - E[r_j])^2}$

$\sigma_j = \sqrt{\sigma_j^2}$

Standart sapma, varyansa ait değerin karekökü olacaktır.

```python
standart_sapma = np.sqrt(varyans) * 100

# veya

standart_sapma = np.std(veriler_df['THYAO'], ddof=1) * 100
```

Standart sapmayı yıllıklandırabiliriz.

```python
standart_sapma_yillik = standart_sapma * np.sqrt(is_gunu)
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['THYAO',standart_sapma,standart_sapma_yillik]],
    headers=['Standart Sapma (Günlük), %','Standart Sapma (Yıllık), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/standart_sapma.PNG)

Yukarıda, 250 ile çarpmak yerine 250'nin karekökü ile çarptık. Bunu aşağıdaki gibi açıklayabiliriz.

$\sigma^2 = N_{isgunu}\sigma_{gunluk}^2, \ \sigma = \sqrt{N_{isgunu}}\sigma_{gunluk}$

### 5.3.2. Üstsel Ağırlıklandırılmış Hareketli Ortalama (EWMA)

EWMA (Exponentially Weighted Moving Average), verilerin zaman içindeki değişimlerini takip etmek ve olaylara hızla tepki verebilmek için kullanılan bir istatistiksel yöntemdir. Önceki verilere daha az ağırlık verirken, daha yeni verilere daha fazla ağırlık vererek hesaplanır.

EWMA hesaplamak için aşağıdaki formül kullanılır:

$EWMA_t = \alpha \ x \ r_t \ + \ (1 \ - \ \alpha) \ x \ EWMA_{t-1}$

$EWMA_t$: Güncel EWMA değeridir. Bu, t zamanındaki EWMA'nın değerini temsil eder.

$\alpha$: Düzeltme faktörü veya ağırlık faktörü olarak isimlendirilen parametredir. 0 ile 1 arasında bir değer alır. Daha yüksek bir $\alpha$ değeri, yeni gözlemlere daha fazla ağırlık verir ve EWMA'nın daha hızlı değişmesine neden olur.

$r_t$: Güncel veri noktası veya gözlem değeridir. Bu, t zamanındaki veriyi temsil eder.

$EWMA_{t-1}$: Önceki EWMA değeri. Bu, t-1 zamanındaki EWMA'nın değerini temsil eder.

Logaritmik getirileri kullanarak EWMA değerini hesaplayalım. Bunun için bir fonksiyon yazabiliriz.

```python
def ewma_volatilite_hesapla(getiri, lambda_deger=0.94):
    getiri_kare = getiri**2
    agirlik = [1 - lambda_deger]

    for i in range(1, len(getiri_kare)):
        agirlik.append(agirlik[i-1] * lambda_deger)

    agirlik_getiri = getiri_kare * np.array(agirlik)
    ewma_varyans = np.sum(agirlik_getiri)
    ewma_volatilite = ewma_varyans**0.5
    return ewma_volatilite
```

Sırasıyla günlük ve yıllık EWMA değerlerine bakalım.

```python
ewma_volatilite_gunluk = ewma_volatilite_hesapla(veriler_df['THYAO']) * 100
ewma_volatilite_yillik = ewma_volatilite_gunluk * np.sqrt(is_gunu)
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['THYAO',ewma_volatilite_gunluk,ewma_volatilite_yillik]],
    headers=['EWMA (Günlük), %','EWMA (Yıllık), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/ewma.PNG)

Hareketli EWMA volatilite hesaplayalım.

```python
test_sayisi = 250
ewma_vol = []

for i in range(test_sayisi, len(veriler_df)):
    veriler_df_alt = veriler_df['THYAO'][i - test_sayisi:i]
    ewma_deger = ewma_volatilite_hesapla(getiri=veriler_df_alt)
    ewma_vol.append(ewma_deger)

veriler_df_ewma = veriler_df.copy()

veriler_df_ewma = veriler_df_ewma.iloc[test_sayisi:, :]
veriler_df_ewma['Tarih'] = veriler_df['Tarih'].iloc[test_sayisi:]
veriler_df_ewma['EWMA_Vol'] = ewma_vol

plt.plot(
    'Tarih',
    'THYAO',
    data=veriler_df_ewma,
    color='blue',
    alpha=.3,
    linewidth=.5,
    label='Logaritmik Getiri'
)
plt.plot(
    'Tarih',
    'EWMA_Vol',
    data=veriler_df_ewma,
    color='red',
    linewidth=1,
    label='Volatilite'
)
plt.axhline(y=0, linewidth=1, color='black')
plt.title('THYAO Hisse Senedine Ait EWMA Volatilite', fontsize=14)
plt.xticks(rotation=45)
plt.legend(fontsize=12)
plt.show()
```

![](/imgs/ewma_volatilite_tarihsel.PNG)

### 5.3.3. Otoregresif Koşullu Değişen Varyans (GARCH)

GARCH (Generalized Autoregressive Conditional Heteroskedasticity), volatilitenin zaman içinde değişebileceğini ve geçmiş volatilitenin gelecekteki volatilite üzerinde etkisi olduğunu kabul eder. Bu model, zaman serisi verilerindeki heteroskedastisiteyi (varyansın değişken olması) ele alır ve varyansın otoregresif bir yapıya sahip olduğunu varsayar.

Bu uygulamada, GARCH(1,1) modelini kullanacağız.

```python
def garch_volatilite_hesapla(getiri):
    model = arch_model(getiri, vol='Garch', p=1, q=1)
    model_fit = model.fit()
    forecast = model_fit.forecast(horizon=1)
    garch_volatilite = np.sqrt(forecast.variance.values[-1, :][0])
    return garch_volatilite
```

Sırasıyla günlük ve yıllık GARCH değerlerine bakalım.

```python
garch_volatilite_gunluk = garch_volatilite_hesapla(veriler_df['THYAO']) * 100
garch_volatilite_yillik = garch_volatilite_gunluk * np.sqrt(is_gunu)
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['THYAO',garch_volatilite_gunluk,garch_volatilite_yillik]],
    headers=['GARCH(1,1) (Günlük), %','GARCH(1,1) (Yıllık), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/garch.PNG)

Hareketli tahmin yapalım.

```python
test_sayisi = 250
garch_tahminler = []

for i in range(test_sayisi, len(veriler_df)):
    train = veriler_df['THYAO'][i - test_sayisi:i]
    garch_model = arch_model(train, vol='Garch', p=1, q=1)
    model_fit = garch_model.fit(disp='off')
    tahmin = model_fit.forecast(horizon=1)
    garch_tahminler.append(np.sqrt(tahmin.variance.values[-1,:][0]))

veriler_df_garch = veriler_df.copy()

veriler_df_garch = veriler_df_garch.iloc[test_sayisi:, :]
veriler_df_garch['Tarih'] = veriler_df['Tarih'].iloc[test_sayisi:]
veriler_df_garch['GARCH_Tahmin'] = garch_tahminler

plt.plot(
    'Tarih',
    'THYAO',
    data=veriler_df_garch,
    color='blue',
    alpha=.3,
    linewidth=.5,
    label='Logaritmik Getiri'
)
plt.plot(
    'Tarih',
    'GARCH_Tahmin',
    data=veriler_df_garch,
    color='red',
    linewidth=1,
    label='Volatilite Tahmini'
)
plt.axhline(y=0, linewidth=1, color='black')
plt.title('THYAO Hisse Senedi GARCH(1,1) Volatilite Tahminleri', fontsize=14)
plt.xticks(rotation=45)
plt.legend(fontsize=12)
plt.show()
```

![](/imgs/garch_volatilite_tarihsel.png)

# 6. Portföy Getirisinin ve Riskinin Ölçülmesi

---

## 6.1. Portföy Getirisi

Elimizde, 200 ₺'den aldığımız 1 lot THYAO ve 40 ₺'den aldığımız 1 lot EREGL hisse senetlerinin olduğunu varsayalım ve bu hisse senetlerini sırasıyla 250 ₺'den ve 70 ₺'den satmış olalım. Bu işlemden karımız ve işlemin getirisi ne olmuştur?

$(P_{THYAO,t} - P_{THYAO,{t-1}}) + (P_{EREGL,t} - P_{EREGL,{t-1}}) = (250₺ - 200₺) + (70₺ - 40₺) = 80₺$ kar.

Getirileri ise bireysel olarak hesaplayalım.

$r_{THYAO} = \frac{P_{THYAO,t}}{P_{THYAO,{t-1}}} - 1 = \frac{250₺}{200₺} - 1 = 0.25$ veya %25 getiri.

$r_{EREGL} = \frac{P_{EREGL,t}}{P_{EREGL,{t-1}}} - 1 = \frac{70₺}{40₺} - 1 = 0.75$ veya %75 getiri.

Peki, portföyün getirisi ($r_p$) ne olmuştur?

Eğer hesapladığımız iki getiriyi toplarsak yanlış hesaplamış oluruz. Yani, portföyün getirisi $\%25 + \%75 = \%100$ değildir.

$r_p \neq \%25 + \%75 = \%100$

Biz, varsayımımızda 200 ₺'den THYAO ve 40 ₺'den EREGL aldık. Her ne kadar EREGL hisse senedinden %75 getiri elde etsek de bu hisse senedinin portföydeki payı $40 / (200 + 40)$ olup %17'dir. Bu mantıkla, EREGL hisse senedinin getiri payı $0.17 x 0.75$ olup %13'tür. Aynı şekilde, THYAO hisse senedinin payı $200 / (200 + 40)$ işleminden %83; getiri payı ise $0.83 x 0.25$ işleminden %21 hesaplanabilir. Sonuç olarak, portföyümüzün getirisini %13 + %21'den %34 buluruz.

$r_p = (\frac{200₺}{200₺ + 40₺}) x \%25 + (\frac{40₺}{200₺ + 40₺}) x \%75 \ = \%34$

O halde, yukarıdaki işlemi nasıl yazabiliriz?

$r_p = \omega_{THYAO} \ x \ r_{THYAO} \ + \ \omega_{EREGL} \ x \ r_{EREGL}$

Yukarıda $\omega$, payı veya ağırlığı temsil etmektedir. Yani örneğimizde bulunan iki hisse senedinin portföyümüzdeki ağırlıklarının temsilidir.

Daha önce karımızı 80₺ olarak hesaplamıştık. Eğer karı toplam yatırıma bölersek yine yaklaşık olarak %34 değerine (portföy getiri) ulaşırız. $80₺ / 240₺$ işlemi %33 değerini verecektir. Yuvarlamalardan dolayı tutmayabilir.

2 varlıklı bir portföy için getiri hesaplamasını aşağıdaki gibi genelleştirebiliriz.

$r_p = \omega_1r_1 + \omega_2r_2$

$\sum_{i=1}^{k}\omega_i = 1$

$r_p:$ Portföy getirisi

$\omega_1, \omega_2:$ Varlıkların ağırlıkları (Tüm ağırlıkların toplamı 1 olmalıdır)

$r_1, r_2:$ Varlıkların getirileri

Daha genel bir ifadeyle, k tane varlığın olduğu bir portföyün getirisini aşağıdaki gibi yazabiliriz.

$r_p = \sum_{i=1}^{k}r_i\omega_i$

## 6.2. Portföy Getirisinin Ölçülmesi

Portföyümüzde şu 10 adet hisse senedi olsun: AEFES, ASELS, BIMAS, EREGL, FROTO, GARAN, PETKM, SISE, THYAO ve TOASO.

```python
semboller=['AEFES.IS', 'ASELS.IS', 'BIMAS.IS', 'EREGL.IS', 'FROTO.IS', 'GARAN.IS', 'PETKM.IS', 'SISE.IS', 'THYAO.IS', 'TOASO.IS']
baslangic_tarih='2018-08-16'
bitis_tarih='2023-07-29'

portfoy = yfinance_veri_cek(
    sembol=semboller,
    baslangic_tarih=baslangic_tarih,
    bitis_tarih=bitis_tarih,
    frekans='1d'
)

portfoy = portfoy.set_index('Tarih')
portfoy.describe()
```

![](/imgs/portfoy_10_ozet.PNG)

Ağırlıkları eşit olacak şekilde belirleyelim.

```python
hisse_senedi_n = len(semboller)
agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
```

Çıktı aşağıdaki gibi olacaktır.

```
[0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
```

Beklenen getiriyi hesaplayacak fonksiyonu yazalım.

```python
def portfoy_getiri(df, agirliklar, yuzde=True, yilliklandir=True, isgunu=250):
    portfoy_beklenen_getiri_gunluk = np.sum(agirliklar * df.mean())

    if yuzde:
        portfoy_beklenen_getiri_gunluk *= 100
    else:
        portfoy_beklenen_getiri_gunluk

    if yilliklandir:
        portfoy_beklenen_getiri_yillik = portfoy_beklenen_getiri_gunluk * isgunu
    else:
        portfoy_beklenen_getiri_yillik = None

    return portfoy_beklenen_getiri_gunluk, portfoy_beklenen_getiri_yillik
```

Çalıştırabiliriz.

```python
portfoy_beklenen_getiri_gunluk, portfoy_beklenen_getiri_yillik = portfoy_getiri(df=portfoy, agirliklar=agirliklar)
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['Portföy-10',portfoy_beklenen_getiri_gunluk,portfoy_beklenen_getiri_yillik]],
    headers=['Beklenen Getiri (Günlük), %','Beklenen Getiri (Yıllık), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/portfoy_beklenen_getiri.PNG)

Hisse senetlerinin beklenen getirilerini de hesaplayalım.

```python
hisse_senedi_beklenen_getiri = (portfoy.mean() * is_gunu) * 100
```

![](/imgs/hisse_bireysel_beklenen_getiriler.PNG)

Şimdi görselleştirebiliriz.

```python
df_portfoy_10 = {
    'Hisse Senedi': portfoy.columns,
    'Beklenen Getiri': hisse_senedi_beklenen_getiri
}
df_portfoy_10 = pd.DataFrame(df_portfoy_10).reset_index(drop=True)
df_portfoy_10_portfoy = pd.DataFrame({'Hisse Senedi': ['PORTFÖY-10'], 'Beklenen Getiri': [portfoy_beklenen_getiri_yillik]})
df_portfoy_10 = pd.concat([df_portfoy_10, df_portfoy_10_portfoy]).reset_index(drop=True)

df_portfoy_10_sirala = df_portfoy_10.sort_values(by='Beklenen Getiri')
plt.barh(
    'Hisse Senedi',
    'Beklenen Getiri',
    data=df_portfoy_10_sirala,
    color=['red' if x == 'PORTFÖY-10' else 'gray' for x in df_portfoy_10_sirala['Hisse Senedi']]
)
plt.xlabel('Yıllıklandırılmış Beklenen Getiri', fontsize = 12)
plt.title('Hisse Senetleri ve Portföy Beklenen Getirileri', fontsize = 14)
plt.show()
```

![](/imgs/hisse_portfoy_beklenen_getiri.PNG)

## 6.3. Portföy Riski

Portföy getirisinde olduğu gibi portföy riskinde de risk için hesapladığımız standart sapmaları toplayıp portföy riskine ulaşamayız.

İki varlıklı portföyün riskini aşağıdaki gibi yazabiliriz.

$\sigma_p^2 = \omega_1^2\sigma_1^2 \ + \ \omega_2^2\sigma_2^2 \ + \ 2\omega_1\omega_2\sigma_{1,2}$

Yukarıda, $\omega_1^2\sigma_1^2$ birinci varlığın risk payını, $\omega_2^2\sigma_2^2$ ikinci varlığın risk payını ve $2\omega_1\omega_2\sigma_{1,2}$ iki varlık arasındaki ilişkiyi (kovaryans dahil) temsil etmektedir.

Standart sapma ise aşağıdaki gibi olacaktır.

$\sqrt{\sigma_p^2} = \sigma_p = \sqrt{\omega_1^2\sigma_1^2 \ + \ \omega_2^2\sigma_2^2 \ + \ 2\omega_1\omega_2\sigma_{1,2}}$

Örneğin, portföyümüzde bulunan 1 lot THYAO ve 1 lot EREGL hisse senetlerinin ağırlıkları %60 ve %40, standart sapmaları %30 ve %25 ve kovaryans değeri 0.0005 olsun. Bu portföyün riski ne olur?

$\sigma_p^2 = \omega_{THYAO}^2\sigma_{THYAO}^2 \ + \ \omega_{EREGL}^2\sigma_{EREGL}^2 \ + \ 2\omega_{THYAO}\omega_{EREGL}\sigma_{THYAO,EREGL}$

$\sigma_p^2 = 0.6^2 x 0.3^2 \ + \ 0.4^2 x 0.25^2 \ + \ 2 x 0.6 x 0.4 x 0.0005 = 0.043$

$\sqrt{\sigma_p^2} = \sigma_p = \sqrt{0.043} = 0.21$ veya %21'dir. Eğer portföy tek varlıktan oluşturulsaydı portföyün riski %30 (THYAO) veya %25 (EREGL) olacaktı ancak çeşitlendirme etkisi ile portföy riski %21 olmuştur.

Portföydeki varlık sayısı üç olduğunda portföyün riski aşağıdaki gibi olacaktır.

$\sigma_p^2 = \omega_1^2\sigma_1^2 \ + \ \omega_2^2\sigma_2^2 \ + \ \omega_3^2\sigma_3^2 \ + \ 2\omega_1\omega_2\sigma_{1,2} + \ 2\omega_1\omega_3\sigma_{1,3} + \ 2\omega_2\omega_3\sigma_{2,3}$

Varyansın karekökünü aldığımızda standart sapmaya ulaşıyorduk.

$\sqrt{\sigma_p^2} = \sigma_p = \sqrt{\omega_1^2\sigma_1^2 \ + \ \omega_2^2\sigma_2^2 \ + \ \omega_3^2\sigma_3^2 \ + \ 2\omega_1\omega_2\sigma_{1,2} + \ 2\omega_1\omega_3\sigma_{1,3} + \ 2\omega_2\omega_3\sigma_{2,3}}$

Portföyde k adet varlık söz konusu olduğu zaman aşağıdaki gibi yazabiliriz.

$\sigma_p^2 = \Omega^T \sum \Omega$

Burada, $\Omega$ ağırlıkların vektörünü, $R$ getirilerin matrisini ve $\sum$ varyans-kovaryans matrisini temsil etmektedir.

## 6.4. Portföy Riskinin Ölçülmesi

Portföyümüzde şu 10 adet hisse senedi olsun: AEFES, ASELS, BIMAS, EREGL, FROTO, GARAN, PETKM, SISE, THYAO ve TOASO.

```python
semboller=['AEFES.IS', 'ASELS.IS', 'BIMAS.IS', 'EREGL.IS', 'FROTO.IS', 'GARAN.IS', 'PETKM.IS', 'SISE.IS', 'THYAO.IS', 'TOASO.IS']
baslangic_tarih='2018-08-16'
bitis_tarih='2023-07-29'

portfoy = yfinance_veri_cek(
    sembol=semboller,
    baslangic_tarih=baslangic_tarih,
    bitis_tarih=bitis_tarih,
    frekans='1d'
)

portfoy = portfoy.set_index('Tarih')
portfoy.describe()
```

![](/imgs/portfoy_10_ozet.PNG)

Ağırlıkları eşit olacak şekilde belirleyelim.

```python
hisse_senedi_n = len(semboller)
agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
```

Çıktı aşağıdaki gibi olacaktır.

```
[0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
```

Riski hesaplayacak fonksiyonu yazalım.

```python
def portfoy_risk(df, agirliklar, yuzde=True, yilliklandir=True, isgunu=250):
    varkov_matris = df.cov()
    portfoy_varyans = np.dot(np.transpose(agirliklar), np.dot(varkov_matris, agirliklar))
    portfoy_standart_sapma_gunluk = np.sqrt(portfoy_varyans)

    if yuzde:
        portfoy_standart_sapma_gunluk *= 100
    else:
        portfoy_standart_sapma_gunluk

    if yilliklandir:
        portfoy_standart_sapma_yillik = portfoy_standart_sapma_gunluk * np.sqrt(isgunu)
    else:
        portfoy_standart_sapma_yillik = None

    return portfoy_standart_sapma_gunluk, portfoy_standart_sapma_yillik
```

Çalıştıralım.

```python
portfoy_standart_sapma_gunluk, portfoy_standart_sapma_yillik = portfoy_risk(df=portfoy, agirliklar=agirliklar)
```

Sonuçları bir tabloda toparlayalım.

```python
print(tabulate(
    [['Portföy-10',portfoy_standart_sapma_gunluk,portfoy_standart_sapma_yillik]],
    headers=['Risk (Günlük), %','Risk (Yıllık), %'],
    tablefmt='fancy_grid',
    stralign='center',
    numalign='center',
    floatfmt='.1f'
))
```

![](/imgs/portfoy_risk.PNG)

Hisse senedi özelinde de standart sapmalara bakalım.

```python
hisse_senedi_standart_sapma = (np.std(portfoy) * np.sqrt(is_gunu)) * 100
```

![](/imgs/portfoy_10__standart_sapma.PNG)

Yukarıda görüldüğü üzere çeşitlendirilmiş portföyün standart sapması hisse senetlerinin bireysel standart sapmalarından daha düşüktür.

Standart sapmaları görselleştirelim.

```python
df_portfoy_10 = {
    'Hisse Senedi': portfoy.columns,
    'Standart Sapma': hisse_senedi_standart_sapma
}
df_portfoy_10 = pd.DataFrame(df_portfoy_10).reset_index(drop=True)
df_portfoy_10_portfoy = pd.DataFrame({'Hisse Senedi': ['PORTFÖY-10'], 'Standart Sapma': [portfoy_standart_sapma_yillik]})
df_portfoy_10 = pd.concat([df_portfoy_10, df_portfoy_10_portfoy]).reset_index(drop=True)

df_portfoy_10_sirala = df_portfoy_10.sort_values(by='Standart Sapma')
plt.barh(
    'Hisse Senedi',
    'Standart Sapma',
    data=df_portfoy_10_sirala,
    color=['red' if x == 'PORTFÖY-10' else 'gray' for x in df_portfoy_10_sirala['Hisse Senedi']]
)
plt.xlabel('Yıllıklandırılmış Standart Sapma', fontsize = 12)
plt.title('Hisse Senetleri ve Portföy Standart Sapmaları', fontsize = 14)
plt.show()
```

![](/imgs/hisse_portfoy_standart_sapma.PNG)

## 6.5. Portföyün Çeşitlendirilmesi ve Riskin Düşürülmesi

Portföyün çeşitlendirilmesi ve riskin düşürülmesi, yatırımcıların portföylerini farklı varlık sınıflarında ve farklı şirketlerin hisse senetlerinde çeşitlendirerek risklerini dağıtmalarını ifade eder. Böylelikle, yatırımcılar tek bir hisse senedine veya sektöre aşırı şekilde bağımlı olmaktan kaçınarak portföylerini daha dengeli hale getirirler.

Örneğimizde, AEFES, ASELS, BIMAS, EREGL, FROTO, GARAN, PETKM, SISE, THYAO ve TOASO olmak üzere 10 adet hisse senedini almıştık. Portföyümüze hisse senedi ekledikçe riskin ne olabileceğine bakalım.

Bunun için öncelikle hisseleri birer artırarak portföye ekleyelim.

```python
hisse_senetleri = [s.replace('.IS','') for s in semboller]
portfoyler = []
for i in range(1, len(hisse_senetleri) + 1):
    portfoyler.append(hisse_senetleri[0:i])
```

Çıktı aşağıdaki gibi olacaktır.

```
[['AEFES'], ['AEFES', 'ASELS'], ['AEFES', 'ASELS', 'BIMAS'], ['AEFES', 'ASELS', 'BIMAS', 'EREGL'], ['AEFES', 'ASELS', 'BIMAS', 'EREGL', 'FROTO'], ['AEFES', 'ASELS', 'BIMAS', 'EREGL', 'FROTO', 'GARAN'], ['AEFES', 'ASELS', 'BIMAS', 'EREGL', 'FROTO', 'GARAN', 'PETKM'], ['AEFES', 'ASELS', 'BIMAS', 'EREGL', 'FROTO', 'GARAN', 'PETKM', 'SISE'], ['AEFES', 'ASELS', 'BIMAS', 'EREGL', 'FROTO', 'GARAN', 'PETKM', 'SISE', 'THYAO'], ['AEFES', 'ASELS', 'BIMAS', 'EREGL', 'FROTO', 'GARAN', 'PETKM', 'SISE', 'THYAO', 'TOASO']]
```

Portföye önce AEFES, sonra AEFES-ASELS, sonra AEFES-ASELS-BIMAS eklendi ve bu şekilde devam etmektedir. Şimdi her bir portföyün riskini daha önce hesapladığımız gibi hesaplayabiliriz.

```python
portfoyler_risk = []
for p in portfoyler:
    df = portfoy[p]

    hisse_senedi_n = len(df.columns)
    agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
    varkov_matris = df.cov()

    portfoy_varyans = np.dot(np.transpose(agirliklar), np.dot(varkov_matris, agirliklar))
    portfoy_standart_sapma = np.sqrt(portfoy_varyans)
    portfoy_standart_sapma_yillik = portfoy_standart_sapma * np.sqrt(is_gunu)

    portfoyler_risk.append(portfoy_standart_sapma_yillik)
```

Çıktı aşağıdaki gibi olacaktır.

```
[0.3874127756261798,
 0.34201414234857913,
 0.29175300863030074,
 0.2835333625137374,
 0.2856976141596776,
 0.2839223650934056,
 0.28529635012630866,
 0.2874982241043029,
 0.29190074231683183,
 0.2923724379922857]
```

Görselleştirelim ve riskin portföye hisse senedi eklendikçe nasıl değiştiğini görelim.

```python
df_portfoyler_risk = pd.DataFrame({
    'HisseSenediSayisi': range(1, len(portfoyler) + 1),
    'YillikStandartSapma': portfoyler_risk
})

plt.plot(
    'HisseSenediSayisi',
    'YillikStandartSapma',
    data=df_portfoyler_risk
)
plt.title('Hisse Senedi Sayısı ve Risk (Yıllıklandırılmış Standart Sapma)', fontsize=13)
plt.show()
```

![](/imgs/hisse_senedi_sayisi_risk_cesitlendirme.png)

Riskin, %39'dan başlayıp %34'e düştüğünü, ardından %28'lerde bir süre gidip son iki portföyde %29'lara bir miktar çıktığını görüyoruz. Çok genel bir ifadeyle, çeşitlendirme arttıkça riskin düştüğünü söyleyebiliriz ancak bu bizim örneğimizde hisse senedi ekledikçe riskin sürekli düşeceği anlamına gelmeyecek.

## 6.6. Portföyde Hedeflenen Beklenen Getiriye Göre Ağırlıkların Optimize Edilmesi

Portföyde ağırlıkların optimize edilmesi, bir yatırım portföyünün bileşen varlıklarının optimal dağılımını belirlemeyi ifade eder.

Portföyümüzde, `THYAO` ve `EREGL` hisse senetleri olsun. Hisse senetlerinin beklenen getirilerinin sırasıyla %55 ve %25 olduğunu ve beklediğimiz getirinin ise %35 olduğunu varsayalım.

Portföyün beklenen getirisi şudur:

$E[r_p] = \omega_1 E[r_1] + \omega_2 E[r_2]$

Portföyümüzdeki hisse senetleri ile yazalım.

$E[r_p] = \omega_{THYAO} E[r_{THYAO}] + \omega_{EREGL} E[r_{EREGL}]$

Aşağıdaki gibi tekrar yazabiliriz.

$\sum_{i=1}^{k} \omega_i = 1; \omega_1 + \omega_2 = 1$

$E[r_p] = \omega_{THYAO} E[r_{THYAO}] + (1 - \omega_{THYAO}) E[r_{EREGL}]$

Değerleri yerine koyalım ve gerekli işlemleri yapalım.

$0.35 = \omega_{THYAO} 0.55 + (1 - \omega_{THYAO}) 0.25$

$0.35 = \omega_{THYAO} 0.55 + 0.25 - \omega_{THYAO} 0.25$

$0.35 + \omega_{THYAO} 0.25 = \omega_{THYAO} 0.55 + 0.25$

$\omega_{THYAO} 0.25 - \omega_{THYAO} 0.55 = 0.25 - 0.35$

$-\omega_{THYAO} 0.3 = - 0.1$

$\omega_{THYAO} 0.3 = 0.1$

$\omega_{THYAO} = \frac{0.1}{0.3}$

$\omega_{THYAO} \approx 0.34$

$\omega_{EREGL} = (1 - \omega_{THYAO})$

$\omega_{EREGL} = (1 - 0.34)$

$\omega_{EREGL} \approx 0.66$

Bakalım istediğimiz beklenen getiri olan %35'e ulaşabiliyor muyuz?

$E[r_p] = \omega_1 E[r_1] + \omega_2 E[r_2]$

$E[r_p] = 0.34 x 0.55 + 0.66 x 0.25$

$E[r_p] \approx 0.35 = \%35$

Daha genel bir ifadeyle, yatırımcının beklediği (hedeflenen) getiriyi aşağıdaki gibi yazabiliriz.

$\omega_1 = \frac{E[r_p] - E[r_2]}{E[r_1] - E[r_2]}; \omega_2 = 1 - \omega_1$

Uygulamamıza dönüp seçtiğimiz 10 adet hisse senedinin optimal ağırlıklarını bulalım.

Öncelikle beklenen getirileri hesaplayacak bir fonksiyon yazalım.

```python
def portfoy_getiri(df, agirliklar, is_gunu=250):
    portfoy_beklenen_getiri = np.dot(np.transpose(agirliklar), df.mean()) * is_gunu
    return portfoy_beklenen_getiri
```

Her bir hisse senedinin başlangıç ağırlıkları verelim. Başlangıç ağırlıkları daha önce hesapladığımız gibi eşit olacaktır. Uygulamamızda 10 tane hisse senedi olduğu için her birinin ağırlığı 0.1 olacaktır.

```python
hisse_senedi_n = len(portfoy.columns)
baslangic_agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
```

Test amaçlı portföyümüzün yıllıklandırılmış beklenen getirisi hesaplayalım.

```python
portfoy_getiri(df=portfoy, agirliklar=baslangic_agirliklar, is_gunu=is_gunu)
```

Çıktı aşağıdaki gibi olacaktır.

```
0.4543850368681283
```

Fakat bizim hedeflediğimiz beklenen getirinin 0.5 veya %50 olduğunu varsayalım. Bunun için de bir fonksiyon yazalım.

```python
def optimize_portfoy(df, baslangic_agirliklar, hedeflenen_beklenen_getiri, is_gunu=250):
    def portfoy_getiri(agirliklar):
        portfoy_beklenen_getiri = np.dot(np.transpose(agirliklar), df.mean()) * is_gunu
        return portfoy_beklenen_getiri

    hisse_senedi_n = len(baslangic_agirliklar)
    sinirlar = tuple((0, 1) for i in range(hisse_senedi_n))
    kisitlar = (
        {'type': 'eq', 'fun': lambda w: np.sum(w) - 1},
        {'type': 'eq', 'fun': lambda x: x.dot(df.mean()) * is_gunu - hedeflenen_beklenen_getiri}
    )
    sonuc = minimize(fun=portfoy_getiri, x0=baslangic_agirliklar, bounds=sinirlar, constraints=kisitlar)
    return sonuc
```

Yukarıda ilk satır, her bir ağırlık için 0 ile 1 arasında bir sınırlama belirler. Bu sınırlar, optimize edilen ağırlıkların bu değer aralığı içinde kalmasını sağlar. Böylece, optimize edilen ağırlıklar 0 ile 1 arasında olacak ve bu sınırlara uygun olacak şekilde hesaplanacaktır.

Yukarıda ikinci satırda, ilk kısıt, ağırlıkların toplamının 1 olmasını sağlamak için kullanılmaktadır. `'type': 'eq'` ifadesi, eşitlik kısıtını belirtir. `lambda w: np.sum(w) - 1` ifadesi ise ağırlıkların toplamının 1 olmasını kontrol eden bir fonksiyon tanımlar. Bu fonksiyonun sonucunun 0 olması beklenir. İkinci kısıt, hedeflenen beklenen getiri değerini kontrol etmek için kullanılır. `'type': 'eq'` ifadesi yine eşitlik kısıtını belirtir. `lambda x: x.dot(df.mean()) * is_gunu - hedeflenen_beklenen_getiri` ifadesi, ağırlıkların beklenen getirisiyle hedeflenen getiri değeri arasındaki farkı kontrol eden bir fonksiyonu temsil eder. Bu fonksiyonun sonucunun 0 olması beklenir.

Çalıştıralım.

```python
hisse_senedi_n = len(portfoy.columns)
baslangic_agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n

sonuc = optimize_portfoy(
    df=portfoy,
    baslangic_agirliklar=baslangic_agirliklar,
    hedeflenen_beklenen_getiri=0.5,
    is_gunu=is_gunu
)
```

Çıktı aşağıdaki gibi olacaktır.

```
message: Optimization terminated successfully
 success: True
  status: 0
     fun: 0.49999999992878136
       x: [ 6.018e-02  5.711e-02  8.394e-02  7.085e-02  1.781e-01
            8.641e-02  4.517e-02  1.123e-01  1.385e-01  1.674e-01]
     nit: 2
     jac: [ 3.636e-01  3.566e-01  4.178e-01  3.879e-01  6.325e-01
            4.234e-01  3.293e-01  4.825e-01  5.422e-01  6.081e-01]
    nfev: 22
    njev: 2
```

Çıktıda, `fun` hedeflenen beklenen getiriyi ve `x` ağırlıkları göstermektedir. Bu ağırlıklar ile portföyümüzün beklenen getirisini alalım ki bu değeri 0.5 veya %50 bekliyoruz.

```python
portfoy_getiri(df=portfoy, agirliklar=sonuc['x'], is_gunu=is_gunu)
```

Çıktı, `0.49999999992878136` olacaktır.

Hisse senetlerinin aldığı ağırlıkları görselleştirelim.

```python
df_portfoy_agirliklar = pd.DataFrame({
    'HisseSenedi': portfoy.columns,
    'Agirlik': sonuc['x']
})

df_portfoy_agirliklar_sirala = df_portfoy_agirliklar.sort_values(by='Agirlik')
plt.barh(
    'HisseSenedi',
    'Agirlik',
    data=df_portfoy_agirliklar_sirala
)
plt.xlabel('Ağırlık', fontsize = 12)
plt.title('Hisse Senetleri ve Optimal Ağırlıkları', fontsize = 14)
plt.figtext(1, -0.05, 'Hedeflenen Beklenen Getiri %50', fontsize=10, ha='right', color='gray')
plt.show()
```

![](/imgs/hisse_senedi_getiri_optimal_agirlik.png)

## 6.7. Portföy Riskinin Ağırlıkların Optimize Edilmesi ile Minimize Edilmesi

Portföy riskinin minimize edilmesi, yatırımcının portföyündeki risk düzeyini azaltmayı hedefleyen bir stratejidir.

Portföyümüzde, `THYAO` ve `EREGL` hisse senetleri olsun. Hisse senetlerinin toplam risklerinin sırasıyla %45 ve %35 ve kovaryanslarının 0.0005 olduğunu varsayalım. Riski minimize eden bir portföy yapalım.

Portföyün riski aşağıdaki gibi hesaplanır.

$\sigma_p^2 = \omega_1^2 \sigma_1^2 + \omega_2^2 \sigma_2^2 + 2\omega_1 \omega_2 \sigma_{1,2}$

Hisse senetlerini yerine koyalım.

$\sigma_p^2 = \omega_{THYAO}^2 \sigma_{THYAO}^2 + \omega_{EREGL}^2 \sigma_{EREGL}^2 + 2\omega_{THYAO} \omega_{EREGL} \sigma_{THYAO,EREGL}$

Toplam riskleri de yerleştirelim.

$\sigma_p^2 = \omega_{THYAO}^2 0.45^2 + \omega_{EREGL}^2 0.35^2 + 2\omega_{THYAO} \omega_{EREGL} 0.0005$

Risk aşağıda minimize olacaktır.

$\omega_1* = \frac{\sigma_2^2 - \sigma_{1,2}}{\sigma_1^2 + \sigma_2^2 - 2\sigma_1\sigma_2} \equiv \omega_{THYAO}*$

$\omega_{THYAO}* = \frac{\sigma_{EREGL}^2 - \sigma_{THYAO,EREGL}}{\sigma_{THYAO}^2 + \sigma_{EREGL}^2 - 2\sigma_{THYAO,EREGL}}$

Değerleri yerine koyalım.

$\omega_{THYAO}* = \frac{0.35^2 - 0.0005}{0.45^2 + 0.35^2 - 2(0.0005)}$

$\omega_{THYAO}* \approx 0.38$

$\omega_{EREGL}* = 1 - \omega_{THYAO}*$

$\omega_{EREGL}* = 1 - 0.38$

$\omega_{EREGL}* \approx 0.62$

Portföyün riskine bakalım.

$\sigma_p^2 = \omega_1^2 \sigma_1^2 + \omega_2^2 \sigma_2^2 + 2\omega_1 \omega_2 \sigma_{1,2}$

$\sigma_p^2 = 0.38^2 0.45^2 + 0.62^2 0.35^2 + 2 x 0.38 x 0.62 x 0.0005$

$\sigma_p^2 = (0.38^2 x 0.45^2) + (0.62^2 x 0.35^2) + (2 x 0.38 x 0.62 x 0.0005)$

$\sigma_p^2 \approx 0.077$

Varyansını bulduk. Standart sapmasına bakalım.

$\sqrt{\sigma_p^2} = \sqrt{0.07656560000000001}$

$\sigma_p \approx 0.28 = \%28$

Bulduğumuz risk, hisse senetlerinin kendi risklerinden daha düşük çıkmıştır.

Uygulamamıza dönüp seçtiğimiz 10 adet hisse senedinden oluşturduğumuz portföyün riskini minimize edelim.

```python
def portfoy_risk(df, agirliklar, is_gunu=250):
    varkov_matris = df.cov()

    portfoy_varyans = np.dot(np.transpose(agirliklar), np.dot(varkov_matris, agirliklar))
    portfoy_standart_sapma = np.sqrt(portfoy_varyans)
    portfoy_standart_sapma_yillik = portfoy_standart_sapma * np.sqrt(is_gunu)

    return portfoy_standart_sapma_yillik
```

Optimize edecek bir fonksiyon yazalım.

```python
def optimize_portfoy(df, hedeflenen_beklenen_getiri, is_gunu=250):
    hisse_senedi_n = len(df.columns)
    baslangic_agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
    sinirlar = tuple((0, 1) for i in range(hisse_senedi_n))
    kisitlar = ({'type': 'eq', 'fun': lambda w: np.sum(w) - 1})

    def portfoy_getiri(agirliklar):
        portfoy_beklenen_getiri = np.dot(np.transpose(agirliklar), df.mean()) * is_gunu
        return portfoy_beklenen_getiri

    def portfoy_risk(agirliklar):
        varkov_matris = df.cov()
        portfoy_varyans = np.dot(np.transpose(agirliklar), np.dot(varkov_matris, agirliklar))
        portfoy_standart_sapma = np.sqrt(portfoy_varyans)
        portfoy_standart_sapma_yillik = portfoy_standart_sapma * np.sqrt(is_gunu)
        return portfoy_standart_sapma_yillik

    sonuc = minimize(fun=portfoy_risk, x0=baslangic_agirliklar, bounds=sinirlar, constraints=kisitlar)
    return sonuc
```

Çalıştıralım.

```python
hisse_senedi_n = len(portfoy.columns)

sonuc = optimize_portfoy(
    df=portfoy,
    hedeflenen_beklenen_getiri=0.5,
    is_gunu=is_gunu
)
```

Çıktı aşağıdaki gibi olacaktır.

```
message: Optimization terminated successfully
 success: True
  status: 0
     fun: 0.2677300832650254
       x: [ 1.882e-01  2.601e-02  3.896e-01  1.481e-01  4.878e-02
            8.505e-02  4.819e-02  1.800e-02  6.370e-19  4.797e-02]
     nit: 7
     jac: [ 2.675e-01  2.676e-01  2.679e-01  2.679e-01  2.677e-01
            2.675e-01  2.676e-01  2.679e-01  2.701e-01  2.676e-01]
    nfev: 77
    njev: 7
```

Çıktıda, `fun` portföyün riskini ve `x` ağırlıkları göstermektedir.

Hisse senetlerini eşit ağırlıklar ile portföye ekleseydik alacağımız risk aşağıdaki gibi olacaktı.

```python
portfoy_risk(df=portfoy, agirliklar=baslangic_agirliklar, is_gunu=is_gunu)
```

Çıktı, `0.2923724379922857` olacaktır. Yani, %29.2'lik bir risk ölçtük.

```python
portfoy_risk(df=portfoy, agirliklar=sonuc['x'], is_gunu=is_gunu)
```

Hisse senetlerini, ağırlıklarını optimize ederek portföye eklersek de alacağımız risk `0.2677300832650254` olacaktır. Yani, %26.8 risk olup eşit ağırlıklı portföyden daha azdır.

Hisse senetlerinin aldığı ağırlıkları görselleştirelim.

```python
df_portfoy_agirliklar = pd.DataFrame({
    'HisseSenedi': portfoy.columns,
    'Agirlik': sonuc['x']
})

df_portfoy_agirliklar_sirala = df_portfoy_agirliklar.sort_values(by='Agirlik')
plt.barh(
    'HisseSenedi',
    'Agirlik',
    data=df_portfoy_agirliklar_sirala
)
plt.xlabel('Ağırlık', fontsize = 12)
plt.title('Hisse Senetleri ve Optimal Ağırlıkları', fontsize = 14)
plt.figtext(1, -0.05, 'Portföy riski minimize edilmiştir', fontsize=10, ha='right', color='gray')
plt.show()
```

![](/imgs/hisse_senedi_risk_optimal_agirlik.png)

# 7. Etkin Sınır

---

## 7.1. Etkin Sınır Nedir?

Modern Portföy Teorisi (MPT) tarafından öne sürülen etkin sınır, farklı varlıkların veya yatırımların farklı getiri ve risk profillerine sahip olduğu durumlarda, bu varlıkların farklı ağırlıklarla bir araya getirilerek en iyi toplam portföyün elde edilebileceği bir grafiksel gösterimdir. Etkin sınır, yatırımcıların risk ve getiri tercihlerini dikkate alarak en iyi portföy kombinasyonunu belirlemelerine yardımcı olur.

Etkin sınır, iki temel bileşenin birleşiminden oluşur:

i. Verimlilik Çizgisi (Efficient Frontier): Bu, farklı risk düzeylerinde elde edilebilecek maksimum getiriyi temsil eden bir eğridir. Daha yüksek getiri için daha fazla risk almak gerektiği, düşük riskle ancak daha düşük getiriyle daha güvenli yatırımlar yapılabileceği şeklinde ifade edilebilir.

ii. Riskli Varlıkların ve Risk-Free Varlığın (Risk-Free Asset) Birleşimi: Etkin sınır, riskli varlıkların (örneğin, hisse senetleri veya tahviller gibi) belirli ağırlıklarla birleştirilmesiyle elde edilebilecek portföyleri gösterir. Ayrıca, riskli varlıklarla risksiz bir varlık (genellikle riskli olmayan devlet tahvilleri gibi kabul edilir) arasında bir bileşim de içerir. Böylece, belirli bir risk düzeyinde yatırımcıların bekledikleri maksimum getiriyi elde edebilecekleri noktalar etkin sınıra denk gelir.

## 7.2. Etkin Sınır ve En İyi Portföyün Bulunması

Türk borsasından çıkalım ve bu uygulamada S&P 500 endeksinden şu 10 adet hisse senedini kullanalım: AAPL, AMZN, GOOGL, META, MSFT, NFLX, NVDA, TSLA, WMT ve XOM.

Risksiz faiz oranını 0 varsayalım.

```python
semboller=['AAPL', 'AMZN', 'GOOGL', 'META', 'MSFT', 'NFLX', 'NVDA', 'TSLA', 'WMT', 'XOM']
baslangic_tarih='2018-08-08'
bitis_tarih='2023-07-29'

portfoy = yfinance_veri_cek(
    sembol=semboller,
    baslangic_tarih=baslangic_tarih,
    bitis_tarih=bitis_tarih,
    frekans='1d'
)

portfoy = portfoy.set_index('Tarih')
```

Uygulamada 5000 adet portföy oluşturacağız. Portföylerde yer alan hisse senetlerine ait ağırlıklar rassal seçilecek.

```python
np.random.seed(34)
portfoy_sayisi = 5000
tum_agirliklar = np.zeros((portfoy_sayisi, len(portfoy.columns)))
getiriler = np.zeros(portfoy_sayisi)
riskler = np.zeros(portfoy_sayisi)
sharpe_oranlari = np.zeros(portfoy_sayisi)

for i in range(portfoy_sayisi):
    agirliklar = np.array(np.random.random(len(portfoy.columns)))
    agirliklar = agirliklar / np.sum(agirliklar)
    tum_agirliklar[i,:] = agirliklar

    getiriler[i] = np.sum((portfoy.mean() * agirliklar * is_gunu))
    riskler[i] = np.sqrt(np.dot(agirliklar.T, np.dot(portfoy.cov() * is_gunu, agirliklar)))
    sharpe_oranlari[i] = getiriler[i] / riskler[i]
```

Maksimum Sharpe Oranı ve bu oranın konumuna bakalım.

```python
print(f'Maksimum Sharpe Oranı: {sharpe_oranlari.max()}')
print(f'Maksimum Sharpe Oranının Konumu: {sharpe_oranlari.argmax()}')
```

Çıktı aşağıdaki gibi olacaktır.

```
Maksimum Sharpe Oranı: 0.8934701385137666
Maksimum Sharpe Oranının Konumu: 3269
```

Yani, en iyi portföyün ~0.89 Sharpe oranı ile 3269. indekste olduğunu söyleyebiliriz. Bu indeks ya da portföydeki hisse senetlerine ait ağırlıklara bakalım.

```python
print(tum_agirliklar[sharpe_oranlari.argmax(), :])
```

Çıktı aşağıdaki gibi olacaktır.

```
[0.1554362  0.01960557 0.04405643 0.00208792 0.06859701 0.01086181
 0.01673748 0.23522273 0.29690283 0.15049203]
```

Etkin sınıra bakalım.

```python
maks_sharpe_getiri = getiriler[sharpe_oranlari.argmax()]
maks_sharpe_risk = riskler[sharpe_oranlari.argmax()]

plt.scatter(
    riskler,
    getiriler,
    c = sharpe_oranlari,
    cmap='viridis'
)
plt.colorbar(label='Sharpe Oranı')
plt.xlabel('Risk')
plt.ylabel('Getiri')
plt.scatter(
    maks_sharpe_risk,
    maks_sharpe_getiri,
    c='red',
    s=50
)
plt.show()
```

![](/imgs/sharpe_portfoy_simulasyon.png)

Portföy ağırlıklarını optimize edelim.

Önce aşağıdaki fonksiyonları tanımlayacağız.

i. Getiri, risk ve sharpe oranını veren fonksiyon

ii. Negatif Sharpe Oranını hesaplayan fonksiyon

iii. Ağırlıkların toplamını kontrol edecek fonksiyon

```python
def getiri_risk_sharpe(agirliklar):
    agirliklar = np.array(agirliklar)
    getiri = np.sum(portfoy.mean() * agirliklar) * is_gunu
    risk = np.sqrt(np.dot(agirliklar.T, np.dot(portfoy.cov() * is_gunu, agirliklar)))
    sharpe_orani = getiri / risk

    return np.array([getiri, risk, sharpe_orani])

def negatif_sharpe(agirliklar):
    return -getiri_risk_sharpe(agirliklar=agirliklar)[2]

def agirlik_toplam_kontrol(agirliklar):
    return np.sum(agirliklar) - 1
```

Kısıtları oluşturalım.

```python
hisse_senedi_n = len(portfoy.columns)
kisitlar = ({'type': 'eq', 'fun': agirlik_toplam_kontrol})
sinirlar = tuple((0, 1) for i in range(hisse_senedi_n))
baslangic_agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
```

Çalıştıralım.

```python
sonuc = minimize(fun=negatif_sharpe, x0=baslangic_agirliklar, method='SLSQP', bounds=sinirlar, constraints=kisitlar)
```

Çıktı aşağıdaki gibi olacaktır.

```
message: Optimization terminated successfully
 success: True
  status: 0
     fun: -0.9681806506065556
       x: [ 3.123e-01  1.705e-16  0.000e+00  0.000e+00  2.279e-02
            0.000e+00  1.079e-01  1.652e-01  3.917e-01  1.246e-16]
     nit: 10
     jac: [-1.614e-04  6.205e-01  2.367e-01  4.828e-01  1.081e-04
            7.658e-01  4.973e-05  4.950e-04 -1.000e-04  3.698e-02]
    nfev: 112
    njev: 10
```

Getiri, risk ve Sharpe oranını alalım.

```python
getiri_risk_sharpe(sonuc.x)
```

Çıktı aşağıdaki gibi olacaktır.

```
array([0.26461927, 0.273316  , 0.96818065])
```

Yaklaşık 0.97'lik bir Sharpe oranı almış olduk ki bu ilk bulduğumuz 0.89'luk Sharpe oranından daha yüksektir.

# 8. Portföy Performans Metrikleri

---

Portföy performansı, bir yatırım portföyünün belirli bir zaman aralığında elde ettiği getirinin ölçüsüdür. Bu, portföyde bulunan varlıkların fiyat değişimleri ve elde edilen gelirlerle belirlenir. Yatırımcılar, portföy performansını değerlendirmek için genellikle getiri ve risk metriklerini kullanırlar.

Portföy performanslarını değerlendirirken portföylerin taşıdığı risk düzeyi büyük bir önem arz eder ve bu nedenle getirilerin içerdikleri risk faktörlerine göre düzeltilerek değerlendirilmeleri gerekmektedir.

Metrikleri incelerken şu senaryoda üreteceğimiz verileri kullanacağız: 10 adet hisse senedini kullanarak 10 farklı portföy oluşturacağız. Bu 10 farklı portföy 3 ile 7 arasında bulunan rassal olarak seçilmiş adette hisse senetlerinden oluşacak.

```python
np.random.seed(34)

def rastgele_hisseler():
    semboller = ['AEFES.IS', 'ASELS.IS', 'BIMAS.IS', 'EREGL.IS', 'FROTO.IS', 'GARAN.IS', 'PETKM.IS', 'SISE.IS', 'THYAO.IS', 'TOASO.IS']
    adet = np.random.randint(3, 8)

    return np.random.choice(semboller, adet, replace=False)

portfoyler = []
for i in range(10):
    portfoy_hisseleri = rastgele_hisseler()
    portfoyler.append(portfoy_hisseleri)

baslangic_tarih='2018-08-16'
bitis_tarih='2023-07-29'
frekans = '1d'

portfoy_verileri = []
for portfoy in portfoyler:
    df_portfoy = yfinance_veri_cek(
        sembol=portfoy,
        baslangic_tarih=baslangic_tarih,
        bitis_tarih=bitis_tarih,
        frekans=frekans
    )
    df_portfoy.set_index('Tarih', inplace=True)
    portfoy_verileri.append(df_portfoy)

portfoy_getirileri = []
for df_portfoy in portfoy_verileri:
    df_getiri = np.log(df_portfoy / df_portfoy.shift(1)).dropna()
    portfoy_getirileri.append(df_getiri)
```

## 8.1. Sharpe Oranı

Portföyün getirisi ile risksiz faiz (risksiz getiri) arasındaki fark (ek getiri) portföyün standart sapma ile ölçülen riskine bölünür.

$S = \frac{r_p - r_f}{\sigma_p}$

Portföyün risksiz faiz üzerinde sağlamış olduğu getiri aynı risk düzeyine sahip olan portföyler arasında bir sıralama imkanı verir.

10 adet portföyün Sharpe oranlarını hesaplayıp karşılaştıralım.

```python
portfoy_isimleri = []
sharpe_oranlari = []
for i, portfoy in enumerate(portfoy_getirileri, 1):
    portfoy_isim = f"Portföy_{i}"
    portfoy_isimleri.append(portfoy_isim)

    hisse_senedi_n = len(portfoy.columns)
    agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
    portfoy_beklenen_getiri = np.dot(np.transpose(agirliklar), portfoy.mean()) * is_gunu

    varkov_matris = portfoy.cov()
    portfoy_varyans = np.dot(np.transpose(agirliklar), np.dot(varkov_matris, agirliklar))
    portfoy_standart_sapma = np.sqrt(portfoy_varyans) * np.sqrt(is_gunu)

    sharpe_orani = (portfoy_beklenen_getiri - risksiz_faiz_orani) / portfoy_standart_sapma
    sharpe_oranlari.append(sharpe_orani)

df_sharpe = pd.DataFrame({
    'Portfoy': portfoy_isimleri,
    'Sharpe Orani': sharpe_oranlari
})
```

Görselleştirelim.

```python
df_sharpe_sirala = df_sharpe.sort_values(by='Sharpe Orani')
plt.barh(
    'Portfoy',
    'Sharpe Orani',
    data=df_sharpe_sirala
)
plt.xlabel('Sharpe Oranı', fontsize = 12)
plt.title('Portföyler ve Sharpe Oranları', fontsize = 14)
plt.show()
```

![](/imgs/portfoyler_sharpe_oranlari.png)

## 8.2. Treynor Oranı

Treynor oranının Sharpe oranından farkı, portföy getirisi ile risksiz faiz oranı arasındaki farkın sistematik riski temsil eden beta ($\beta$) katsayısına bölünmesidir.

10 adet portföyün Treynor oranlarını hesaplayıp karşılaştıralım.

```python
portfoy_isimleri = []
treynor_oranlari = []

endeks = ['XU100.IS']
benchmark_veri = yfinance_veri_cek(
    sembol=endeks,
    baslangic_tarih=baslangic_tarih,
    bitis_tarih=bitis_tarih,
    frekans=frekans
)
benchmark_veri['XU100_Getiri'] = np.log(benchmark_veri['XU100'] / benchmark_veri['XU100'].shift(1))
benchmark_veri = benchmark_veri.drop(columns=['XU100']).dropna()
benchmark_veri = benchmark_veri.set_index('Tarih')

for i, portfoy in enumerate(portfoy_getirileri, 1):
    portfoy_isim = f"Portföy_{i}"
    portfoy_isimleri.append(portfoy_isim)

    hisse_senedi_n = len(portfoy.columns)
    agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
    portfoy_beklenen_getiri = np.dot(np.transpose(agirliklar), portfoy.mean()) * is_gunu

    df_birlestir = pd.concat([portfoy, benchmark_veri], axis=1).dropna()
    X = sm.add_constant(df_birlestir.iloc[:, 1])
    y = df_birlestir.iloc[:, 0]
    model = sm.OLS(y, X).fit()
    beta = model.params[1]

    treynor_orani = (portfoy_beklenen_getiri - risksiz_faiz_orani) / beta
    treynor_oranlari.append(treynor_orani)

df_treynor = pd.DataFrame({
    'Portfoy': portfoy_isimleri,
    'Treynor Orani': treynor_oranlari
})
```

Görselleştirelim.

```python
df_treynor_sirala = df_treynor.sort_values(by='Treynor Orani')
plt.barh(
    'Portfoy',
    'Treynor Orani',
    data=df_treynor_sirala
)
plt.xlabel('Treynor Oranı', fontsize = 12)
plt.title('Portföyler ve Treynor Oranları', fontsize = 14)
plt.show()
```

![](/imgs/portfoyler_treynor_oranlari.png)

# 9. Riske Maruz Değer (VaR)

---

VaR (Value at Risk), bir portföyün belirli bir güven aralığında, belirli bir yatırım vadesinde karşı karşıya kalabileceği en yüksek kaybın parasal değeridir.

VaR, aşağı yönlü riskleri öngörmeyi amaçlayan bir ölçüttür.

$P(r_t < -VaR) = \alpha$

Yukarıda, $r_t$, portföyün t dönemindeki getirisini, $\alpha$ ise %1 ya da %5 gibi olasılık seviyesini göstermektedir. Özetle, gelecek dönem kaybının VaR değerinden daha fazla olma olasılığı $\alpha$ değerine eşittir.

Üç temel VaR yöntemi bulunmaktadır:

i. Parametrik

ii. Tarihsel Simülasyon

iii. Monte Carlo

## 9.1. Parametrik

Portföyde 1 adet hisse senedi olsun.

```python
sembol=['THYAO.IS']
baslangic_tarih='2022-07-28'
bitis_tarih='2023-07-29'
frekans='1d'

portfoy = yfinance_veri_cek(
    sembol = sembol,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
portfoy = portfoy.drop('Tarih', axis=1)
```

Fonksiyonu yazalım.

```python
def var_parametrik(portfoy_deger, getiriler, guven_duzeyi, elde_tutma_suresi):
    portfoy_standart_sapma = np.std(getiriler)
    z_degeri = norm.ppf(guven_duzeyi)
    var = portfoy_deger * portfoy_standart_sapma * z_degeri * np.sqrt(elde_tutma_suresi)

    return var
```

Çalıştıralım.

```python
portfoy_deger=235000
getiriler=portfoy['THYAO']
guven_duzeyi=0.95
elde_tutma_suresi=1

var_parametrik_sonuc = var_parametrik(
    portfoy_deger=portfoy_deger,
    getiriler=getiriler,
    guven_duzeyi=guven_duzeyi,
    elde_tutma_suresi=elde_tutma_suresi
)
print(f"Parametrik VaR: {var_parametrik_sonuc:.2f}")
print(f"{elde_tutma_suresi} gün sonrasının kaybı %{guven_duzeyi*100} olasılıkla {var_parametrik_sonuc:.2f} ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu {var_parametrik_sonuc / portfoy_deger * 100:.2f} ₺'lik bir VaR üretmektedir.")
```

Çıktı aşağıdaki gibi olacaktır.

```
Parametrik VaR: 12754.36
1 gün sonrasının kaybı %95.0 olasılıkla 12754.36 ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu 5.43 ₺'lik bir VaR üretmektedir.
```

Yukarıda 1 günlük elde tutma süresi ile hesapladık. Peki, 10 günlük elde tutma süresi olsaydı ne olurdu?

```python
portfoy_deger=235000
getiriler=portfoy['THYAO']
guven_duzeyi=0.95
elde_tutma_suresi=10

var_parametrik_sonuc = var_parametrik(
    portfoy_deger=portfoy_deger,
    getiriler=getiriler,
    guven_duzeyi=guven_duzeyi,
    elde_tutma_suresi=elde_tutma_suresi
)
print(f"Parametrik VaR: {var_parametrik_sonuc:.2f}")
print(f"{elde_tutma_suresi} gün sonrasının kaybı %{guven_duzeyi*100} olasılıkla {var_parametrik_sonuc:.2f} ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu {var_parametrik_sonuc / portfoy_deger * 100:.2f} ₺'lik bir VaR üretmektedir.")
```

Çıktı aşağıdaki gibi olacaktır.

```
Parametrik VaR: 40332.83
10 gün sonrasının kaybı %95.0 olasılıkla 40332.83 ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu 17.16 ₺'lik bir VaR üretmektedir.
```

Portföyde 10 adet hisse senedi olsun. Hisse senedi sayısı birden fazla olduğu için portföyün standart sapmasını hesaplamamız gerekecektir.

```python
semboller=['AEFES.IS', 'ASELS.IS', 'BIMAS.IS', 'EREGL.IS', 'FROTO.IS', 'GARAN.IS', 'PETKM.IS', 'SISE.IS', 'THYAO.IS', 'TOASO.IS']
baslangic_tarih='2022-07-28'
bitis_tarih='2023-07-29'
frekans='1d'

portfoy = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
portfoy = portfoy.drop('Tarih', axis=1)
```

Fonksiyonu yazalım.

```python
def portfoy_standart_sapma(df, agirliklar):
    varkov_matris = df.cov()
    portfoy_varyans = np.dot(np.transpose(agirliklar), np.dot(varkov_matris, agirliklar))
    portfoy_standart_sapma = np.sqrt(portfoy_varyans)

    return portfoy_standart_sapma

hisse_senedi_n = len(semboller)
agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n

def var_parametrik(portfoy_deger, guven_duzeyi, elde_tutma_suresi):
    portfoy_ss = portfoy_standart_sapma(df=portfoy, agirliklar=agirliklar)
    z_degeri = norm.ppf(guven_duzeyi)
    var = portfoy_deger * portfoy_ss * z_degeri * np.sqrt(elde_tutma_suresi)

    return var
```

Çalıştıralım.

```python
portfoy_deger=100000
guven_duzeyi=0.95
elde_tutma_suresi=1

var_parametrik_sonuc = var_parametrik(
    portfoy_deger=portfoy_deger,
    guven_duzeyi=guven_duzeyi,
    elde_tutma_suresi=elde_tutma_suresi
)
print(f"Parametrik VaR: {var_parametrik_sonuc:.2f}")
print(f"{elde_tutma_suresi} gün sonrasının kaybı %{guven_duzeyi*100} olasılıkla {var_parametrik_sonuc:.2f} ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu {var_parametrik_sonuc / portfoy_deger * 100:.2f} ₺'lik bir VaR üretmektedir.")
```

Çıktı aşağıdaki gibi olacaktır.

```
Parametrik VaR: 4110.93
1 gün sonrasının kaybı %95.0 olasılıkla 4110.93 ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu 4.11 ₺'lik bir VaR üretmektedir.
```

Yukarıda 1 günlük elde tutma süresi ile hesapladık. Peki, 10 günlük elde tutma süresi olsaydı ne olurdu?

```python
portfoy_deger=100000
guven_duzeyi=0.95
elde_tutma_suresi=10

var_parametrik_sonuc = var_parametrik(
    portfoy_deger=portfoy_deger,
    guven_duzeyi=guven_duzeyi,
    elde_tutma_suresi=elde_tutma_suresi
)
print(f"Parametrik VaR: {var_parametrik_sonuc:.2f}")
print(f"{elde_tutma_suresi} gün sonrasının kaybı %{guven_duzeyi*100} olasılıkla {var_parametrik_sonuc:.2f} ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu {var_parametrik_sonuc / portfoy_deger * 100:.2f} ₺'lik bir VaR üretmektedir.")
```

Çıktı aşağıdaki gibi olacaktır.

```
Parametrik VaR: 12999.90
10 gün sonrasının kaybı %95.0 olasılıkla 12999.90 ₺'yi geçmeyecektir. Yüzdesel olarak, alınan 100 ₺'lik hisse pozisyonu 13.00 ₺'lik bir VaR üretmektedir.
```

Parametrik VaR hesaplamasında kullanılan volatilite, standart sapma yerine EWMA, GARCH veya Örtük (Implied) de olabilir.

## 9.2. Tarihsel Simülasyon

Tarihsel simülasyon yöntemi, parametrik yöntemin aksine herhangi bir parametrik dağılım kullanmaz. Bu yöntem ile portföyün son hali geçmiş N zaman boyunca sabit tutulur. Böylece, hipotetik getiriler geçmiş dönem fiyatlarından türetilir.

Tarihsel simülasyonun çalışma sıralaması şöyledir: Portföydeki varlıkların getirileri hesaplanır ve bu getiriler ağırlıklandırılır. Ağırlıklandırılan bu değerler ise portföyün bugünkü değeri ile çarpılıp toplanır. Toplanan değerler arasından en kötü N. değere bakılır. Örneğin, 250 günlük bir seride %99 güven düzeyinde VaR aranıyorsa, bu en kötü %1'inci değer olup 250 x 0.01 sonucundan 2.5'inci değere denk gelmektedir. Burada, farklı yaklaşımlar mevcuttur. Bir yol, 2 ile 3'ün ortalaması alınabilir. Diğer bir yol yukarıya yuvarlamak olabilir.

Portföyde 2 adet hisse senedi olsun.

```python
semboller=['THYAO.IS','EREGL.IS']
baslangic_tarih='2022-07-28'
bitis_tarih='2023-07-29'
frekans='1d'

portfoy = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
portfoy = portfoy.drop('Tarih', axis=1)
```

Fonksiyonu yazalım.

```python
def var_tarihsel_simulasyon(df, agirliklar, portfoy_deger, guven_duzeyi, elde_tutma_suresi):
    portfoy_agirlikli_getiri = (df * agirliklar).sum(axis=1) * portfoy_deger
    portfoy_agirlikli_getiri = portfoy_agirlikli_getiri.sort_values()
    sira = int(len(portfoy_agirlikli_getiri) * (1 - guven_duzeyi))
    en_kotu_n_deger = portfoy_agirlikli_getiri.iloc[sira]
    var = en_kotu_n_deger * np.sqrt(elde_tutma_suresi)

    return var
```

Çalıştıralım.

```python
df=portfoy
hisse_senedi_n = len(semboller)
agirliklar = [1 / hisse_senedi_n] * hisse_senedi_n
portfoy_deger=100000
guven_duzeyi=0.99
elde_tutma_suresi=1

var_tarihsel_simulasyon_sonuc = var_tarihsel_simulasyon(
    df=df,
    agirliklar=agirliklar,
    portfoy_deger=portfoy_deger,
    guven_duzeyi=guven_duzeyi,
    elde_tutma_suresi=elde_tutma_suresi
)

print(f"Tarihsel Simülasyon VaR: {np.abs(var_tarihsel_simulasyon_sonuc):.2f} ₺")
print(f"{elde_tutma_suresi} gün sonrasının kaybı %{guven_duzeyi*100} olasılıkla {np.abs(var_tarihsel_simulasyon_sonuc):.2f} ₺'yi geçmeyecektir.")
```

Çıktı aşağıdaki gibi olacaktır.

```
Tarihsel Simülasyon VaR: 7178.16 ₺
1 gün sonrasının kaybı %99.0 olasılıkla 7178.16 ₺'yi geçmeyecektir.
```

## 9.3. Monte Carlo

Monte Carlo yöntemi, rastgele sayılar üreterek ve olası farklı senaryoları modelleyerek VaR hesaplamalarını gerçekleştirir.

Rastgele sayıları üretmeden önce Cholesky Ayrışımı yöntemine değinmek yerinde olabilir.

Cholesky Ayrışımı, rastgele değişkenleri korelasyonlu olarak simüle etmek için kullanılan bir yöntemdir. Monte Carlo simülasyonunda gerçekte olan ilişkileri daha iyi temsil etmek adına korelasyonu tanıtmak için kullanılır.

```python
semboller=['THYAO.IS','EREGL.IS']
baslangic_tarih='2022-07-28'
bitis_tarih='2023-07-29'
frekans='1d'

portfoy_getiri = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans
)
portfoy_getiri = portfoy_getiri.drop('Tarih', axis=1)

portfoy_fiyat = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = frekans,
    getiri=False
)
portfoy_fiyat = portfoy_fiyat.drop('Tarih', axis=1).iloc[1:].reset_index(drop=True)
```

Korelasyon matrisini hesaplayalım

```python
korelasyon_matrisi = portfoy_getiri.corr()
```

Cholesky faktorizasyonu kullanarak korelasyon matrisine dönüştürelim.

```python
cholesky_faktor = np.linalg.cholesky(korelasyon_matrisi)
```

1 000 adet rastgele getiriler oluşturalım ve korelasyon matrisini kullanarak dönüştürelim.

```python
np.random.seed(34)
simulasyon_n = 1000
rastgele_sayilar = np.random.normal(size=(simulasyon_n, len(portfoy_getiri.columns)))
simulasyon_getiriler = pd.DataFrame(np.matmul(rastgele_sayilar, cholesky_faktor.T), columns=portfoy_getiri.columns, index=range(simulasyon_n))/100
```

Korelasyonu kontrol edelim.

```python
simulasyon_getiriler.corr()
```

Son fiyatları alalım. Çünkü bu fiyatlar üzerinden simülasyon yapacağız.

```python
son_fiyatlar = {}

for sutun in portfoy_fiyat.columns:
    hisse_ismi = sutun
    son_fiyat = portfoy_fiyat[sutun].iloc[-1]
    son_fiyatlar[hisse_ismi] = son_fiyat

hisseler = portfoy_getiri.columns.tolist()
suruklenmeler = [portfoy_getiri[hisse].mean() for hisse in hisseler]
difuzyonlar = [np.std(portfoy_getiri[hisse]) for hisse in hisseler]
```

Elde tutma süresini belirleyelim.

```python
dt = 1
```

GBM hesaplayacak fonksiyonu yazalım.

```python
def gbm(baslangic_fiyat, suruklenme, difuzyon):
    rastgele_sayilar = np.random.normal(size=simulasyon_n)
    getiriler = baslangic_fiyat * (suruklenme * dt) + baslangic_fiyat * (difuzyon * np.sqrt(dt) * rastgele_sayilar)
    return getiriler
```

Hesaplayalım.

```python
for hisse, baslangic_fiyat, suruklenme, difuzyon in zip(hisseler, son_fiyatlar.values(), suruklenmeler, difuzyonlar):
    getiriler = gbm(baslangic_fiyat, suruklenme, difuzyon)
    simulasyon_getiriler[hisse + '_Sim'] = baslangic_fiyat + getiriler
```

VaR hesaplama aşamasına geçebiliriz. Nominal ve portföy değerini belirleyelim.

```python
nominal = 1000
portfoy_deger = sum(son_fiyatlar[hisse_ismi] * nominal for hisse_ismi in son_fiyatlar)
sim_columns = [sutun for sutun in simulasyon_getiriler.columns if sutun.endswith('_Sim')]
simulasyon_getiriler['Portfoy_Sim'] = simulasyon_getiriler[sim_columns].sum(axis=1) * nominal
simulasyon_getiriler['Degisim'] = simulasyon_getiriler['Portfoy_Sim'] - portfoy_deger
```

VaR sonucuna bakalım.

```python
var = np.abs(np.percentile(simulasyon_getiriler['Degisim'].iloc[1:], 1))
print(f"VaR ({dt} günlük elde tutma süresi):", round(var, ndigits=2),"₺'dir.")
```

Çıktı aşağıdaki gibi olacaktır.

```
VaR (1 günlük elde tutma süresi): 17643.19 ₺'dir.
```

# 10. Portföy Optimizasyonu için Python Paketlerinin İncelenmesi

---

## 10.1. PyPortfolioOpt

![](/imgs/py_portfolio_opt.png)

BIST 100'den seçtiğimiz 10 adet hisse senedi ile paketi inceleyelim.

```python
semboller = ['AEFES.IS', 'ASELS.IS', 'BIMAS.IS', 'EREGL.IS', 'FROTO.IS', 'GARAN.IS', 'PETKM.IS', 'SISE.IS', 'THYAO.IS', 'TOASO.IS']
baslangic_tarih = '2018-08-16'
bitis_tarih = '2023-07-29'

portfoy = yfinance_veri_cek(
    sembol = semboller,
    baslangic_tarih = baslangic_tarih,
    bitis_tarih = bitis_tarih,
    frekans = '1d',
    getiri=False
)
portfoy = portfoy.set_index('Tarih')
```

Beklenen getiri ve varyans-kovaryansı hesaplayalım.

```python
beklenen_getiri = expected_returns.mean_historical_return(
    prices = portfoy,
    returns_data = False,
    frequency = 250,
    compounding = False,
    log_returns = True
)
```

Yukarıda, `prices` parametresi verilerin ham halini (fiyatları) almaktadır. Eğer veri seti getirilerden oluşuyorsa `returns_data` parametresi `True` değerini almalıdır. Değeri `False` olursa ham halini kullanacaktır. İş günü varsayılan olarak `252`'dir ancak biz `250` kullandığımız için değiştirebiliriz. Eğer geometrik ortalama hesaplanmak isteniyorsa `compounding` parametresi varsayılan değer olan `True` olarak bırakılmalıdır. Değeri `False` olursa aritmetik olarak hesaplayacaktır. Son parametre olan `log_returns`, fiyatların logaritmik getiri cinsinden hesaplanıp hesaplanmayacığını belirlemektedir. Değeri `True` olursa logaritmik olarak hesaplayacaktır. Aksi halde, `False` olarak ayarlanmalıdır.

```python
beklenen_getiri
```

![](/imgs/py_portfolio_opt_beklenen_getiri.PNG)

```python
varkov_matris = risk_models.sample_cov(
    prices = portfoy,
    returns_data = False,
    frequency = 250,
    log_returns = True
)
```

Yukarıdaki fonksiyonda yer alan parametreler ile bir önceki fonksiyonda yer alan parametreler birbirine benzemektedir. Farklı olarak burada varyans-kovaryans matrisini oluşturduk.

![](/imgs/py_portfolio_opt_varyans_kovaryans.PNG)

Matrisi görselleştirebiliriz.

```python
plotting.plot_covariance(
    cov_matrix=varkov_matris,
    plot_correlation=False,
    show_tickers=True,
)
plt.title('Kovaryans Matrisi')
plt.grid(False)
plt.show()
```

Yukarıdaki fonksiyonda yer alan `plot_correlation` parametresi `False` ise kovaryansı, `True` ise korelasyonu gösterir. `show_tickers` parametresi `True` ise hisse senetlerinin isimlerini gösterir. Değer `False` olarak ayarlandığında ise hisse senetlerinin isimlerini göstermez.

![](/imgs/py_portfolio_opt_kovaryans_grafik.PNG)

`plot_correlation` parametresini `True` yapalım.

```python
plotting.plot_covariance(
    cov_matrix=varkov_matris,
    plot_correlation=True,
    show_tickers=True,
)
plt.title('Korelasyon Matrisi')
plt.grid(False)
plt.show()
```

![](/imgs/py_portfolio_opt_korelasyon_grafik.PNG)

Maksimum Sharpe oranı ile maksimize edelim.

```python
etkin_sinir = EfficientFrontier(
    expected_returns=beklenen_getiri,
    cov_matrix=varkov_matris,
    weight_bounds=(0,1)
)
ham_agirliklar = etkin_sinir.max_sharpe()
temizlenmis_agirliklar = etkin_sinir.clean_weights()
etkin_sinir.portfolio_performance(verbose=True)
```

`etkin_sinir` değişkeninde `expected_returns` parametresi ile portföydeki varlıkların beklenen getirilerini içeren bir diziyi, `cov_matrix` ile portföydeki varlıkların varyans-kovaryans matrisini ve `weight_bounds` ile de portföydeki her bir varlığın ağırlığının (yatırım miktarının) 0 ile 1 arasında olması gerektiğini belirttik. Genel olarak `EfficientFrontier` fonksiyonu, portföy optimizasyonu için kullanılan bir sınıftır ve yukarıda verilen beklenen getiri ve varyans-kovaryans matrisiyle birlikte portföyün etkin sınırını oluşturur.

`max_sharpe()`, etkin sınırdaki en yüksek Sharpe oranına sahip portföy ağırlıklarını bulmayı sağlar. `clean_weights()`, elde edilen portföy ağırlıklarını temizler ve düzenler, böylece küçük ağırlıkları sıfıra yakın değerlere ayarlar. Bu, uygulanabilirlik ve anlaşılabilirlik açısından önemlidir. Son olarak, `portfolio_performance()`, optimize edilmiş portföyün performansını gösterir. İçerisine verdiğimiz `verbose=True` ifadesi, daha fazla detay içeren bilgilerin görüntülenmesini sağlar.

Çıktı aşağıdaki gibi olacaktır.

```
Expected annual return: 52.6%
Annual volatility: 29.8%
Sharpe Ratio: 1.70
(0.5258814133722242, 0.2975661767437558, 1.7000635586612909)
```

%52.6'lık bir beklenen yıllık getiri, %29.8'lik bir yıllık volatilite (risk) ve 1.70'lik bir Sharpe oranı verdiğini görüyoruz. Sharpe oranından, portföyün riskli varlık kullanarak elde ettiği her bir birimlik ek getiri için ortalama olarak 1.70 birimlik risk aldığını okuyabiliriz.

Portföydeki hisse senetlerinin ağırlıklarına da bakalım.

```python
print(temizlenmis_agirliklar)
```

Çıktı aşağıdaki gibi olacaktır.

```
OrderedDict([('AEFES', 0.01151), ('ASELS', 0.0), ('BIMAS', 0.31799), ('EREGL', 0.0), ('FROTO', 0.23069), ('GARAN', 0.05357), ('PETKM', 0.0), ('SISE', 0.04017), ('THYAO', 0.14509), ('TOASO', 0.20098)])
```

Aşağıdaki gibi daha derli toplu da görebiliriz.

```python
hisseler = list(temizlenmis_agirliklar.keys())
agirlik_degerleri = list(temizlenmis_agirliklar.values())

df_portfoy_agirliklar = pd.DataFrame({
    'HisseSenedi': hisseler,
    'Agirlik': agirlik_degerleri
})
```

![](/imgs/py_portfolio_opt_agirliklar.PNG)

Aynı ağırlıkları görselleştirebiliriz.

```python
plotting.plot_weights(weights=temizlenmis_agirliklar)
```

![](/imgs/py_portfolio_opt_temizlenmis_agirliklar.PNG)

Portföy büyüklüğü belirtilerek (örneğimizde 100 000 ₺) hangisinden ne kadarlık bir alım yapılabileceği görülebilir. Öncelikle aşağıdaki gibi her bir hisse senedinin son fiyatını almalıyız.

```python
son_fiyatlar = get_latest_prices(portfoy)
```

![](/imgs/py_portfolio_opt_son_fiyatlar.PNG)

Dağıtalım.

```python
dagitim_yap = DiscreteAllocation(
    weights=temizlenmis_agirliklar,
    latest_prices=son_fiyatlar,
    total_portfolio_value=100000
)
dagitim, kalan = dagitim_yap.greedy_portfolio()
print("Tamsayı Dağılımı:", dagitim)
print("Kalan: {:.2f}₺".format(kalan))
```

Yukarıdaki kod bloğunda, daha önce elde edilen temizlenmiş ağırlıklar ve varlık fiyatları kullanılarak bir tamsayı dağılımı yapılıyor. Amaç, belirli bir toplam portföy değeri içinde varlıklara uygun bir şekilde yatırım yapmaktır.

`DiscreteAllocation` sınıfı, verilen ağırlıklar ve varlık fiyatlarıyla tamsayı dağılımı yapmayı sağlar. `greedy_portfolio()`, portföydeki varlıklara tamsayı birimlerde yatırım yapmak için açgözlü bir algoritma kullanır. Bu yöntem, temizlenmiş ağırlıklara ve fiyatlara dayanarak uygun varlık dağılımını hesaplar. `dagitim`, tamsayılarla ifade edilen varlık dağılımını içeren bir sözlüktür. `kalan`, tamsayı dağılımı sonucunda kullanılmayan tutarı belirtir.

Çıktı aşağıdaki gibi olacaktır.

```
Tamsayı Dağılımı: {'BIMAS': 146, 'FROTO': 24, 'TOASO': 73, 'THYAO': 62, 'GARAN': 126, 'SISE': 81, 'AEFES': 13}
Kalan: 85.20₺
```

`max_sharpe()`, etkin sınırdaki en yüksek Sharpe oranına sahip portföy ağırlıklarını bulmayı sağlıyordu. Tabi, paketin sağladığı tek yöntem bu değil. Minimum oynaklıkta (volatilite) bir portföyü bulmaya çalışan `min_volatility()` yöntemi de kullanılabilir.

İlgili yöntemi kullanmak için aşağıdaki gibi değiştirmemiz yeterli olacaktır.

```python
# ham_agirliklar = etkin_sinir.max_sharpe()
ham_agirliklar = etkin_sinir.min_volatility()
```

Çıktı aşağıdaki gibi olacaktır.

```
Expected annual return: 41.8%
Annual volatility: 26.8%
Sharpe Ratio: 1.49
(0.4184631387690548, 0.2677298014863866, 1.4883032690304208)
```

%41.8'lik bir beklenen yıllık getiri, %26.8'lik bir yıllık volatilite (risk) ve 1.49'luk bir Sharpe oranı verdiğini görüyoruz. Sharpe oranından, portföyün riskli varlık kullanarak elde ettiği her bir birimlik ek getiri için ortalama olarak 1.49 birimlik risk aldığını okuyabiliriz.

Ağırlıklara bakalım.

```python
plotting.plot_weights(weights=temizlenmis_agirliklar)
```

![](/imgs/py_portfolio_opt_temizlenmis_agirliklar_min_volatility.png)

Portföydeki dağılımı yapalım.

```python
son_fiyatlar = get_latest_prices(portfoy)

dagitim_yap = DiscreteAllocation(
    weights=temizlenmis_agirliklar,
    latest_prices=son_fiyatlar,
    total_portfolio_value=10000
)
dagitim, kalan = dagitim_yap.greedy_portfolio()
print("Tamsayı Dağılımı:", dagitim)
print("Kalan: {:.2f}₺".format(kalan))
```

Çıktı aşağıdaki gibi olacaktır.

```
Tamsayı Dağılımı: {'BIMAS': 179, 'AEFES': 207, 'EREGL': 384, 'GARAN': 200, 'FROTO': 5, 'PETKM': 276, 'TOASO': 18, 'ASELS': 35, 'SISE': 34}
Kalan: 13.63₺
```

## 10.2. empyrial

![](/imgs/empyrial.png)

`empyrial` paketi ilk bakışta iki güzelliği ile karşılıyor.

i. Verileri çekmek için ekstradan fonksiyon yazmanıza veya kod çalıştırmanıza gerek yok. Kaynak kodlardan `yfinance` paketini kullandıkları görülebilir.

ii. Portföyü benchmark ile karşılaştırma imkanı sunuyorlar. Benchmark kısaca, bir yatırım portföyünün performansını ölçmek ve değerlendirmek için kullanılan referans bir ölçüttür.

Tüm bunlar `Engine` isimli sınıfta oluyor. O halde, Toronto Menkul Kıymetler Borsası TSX'ten seçtiğimiz şu 10 adet hisse senedi ile paketi incelemeye başlayalım: AC.TO (Air Canada), CNR.TO (Canadian National Railway Company), DOL.TO (Dollarama Inc.), ENB.TO (Enbridge Inc.), NA.TO (National Bank of Canada), QSR.TO (Restaurant Brands International Inc.), RY.TO (Royal Bank of Canada), SHOP.TO (Shopify Inc.), T.TO (TELUS Corporation) ve TD.TO (The Toronto-Dominion Bank). Benchmark'ımız ise S&P/TSX Composite Index olacak.

```python
portfoy = Engine(
    start_date="2018-08-08",
    end_date="2023-07-29",
    portfolio=['AC.TO', 'CNR.TO', 'DOL.TO', 'ENB.TO', 'NA.TO', 'QSR.TO', 'RY.TO', 'SHOP.TO', 'T.TO', 'TD.TO'],
    weights=[0.1]*10,
    benchmark=["^GSPTSE"]
)

empyrial(
    my_portfolio=portfoy,
    rf=0,
    confidence_value=0.95
)
```

Yukarıda, `Engine` sınıfı, hisselerin bir portföy oluşturduğu bir motor oluşturuyor. `start_date` ve `end_date` parametreleri arasında belirtilen tarihler arasında portföyün performansını değerlendirecektir. Bunun yanında, `portfolio` parametresi ile hisseleri, `weights` ile ağırlıkları ve `benchmark` ile referans ölçütünü belirliyoruz.

`empyrial()` fonksiyonunda, `my_portfolio` parametresi `Engine` üzerinden tanımladığınız portföyü temsil eder. `rf` parametresi risksiz faiz oranını temsil eder. `confidence_value` Value-at-Risk (VaR) hesaplamalarında kullanılan güven düzeyini temsil eder. VaR, belirli bir süre içinde ve belirli bir güven düzeyinde portföyün maksimum potansiyel kaybını ölçer. `confidence_value` parametresinin değeri 0.95, fonksiyonun VaR'ı %95 güven düzeyinde hesaplayacağını gösterir.

Çıktıları inceleyelim.

Backtest tablosu:

![](/imgs/empyrial_backtest_tablo.PNG)

* Annual Return (Yıllık Getiri): Portföyün bir yıl içinde elde ettiği ortalama getiri yüzdesidir.
* Cumulative Return (Toplam Getiri): Portföyün başlangıç tarihinden itibaren elde ettiği toplam getiri yüzdesidir.
* Annual Volatility (Yıllık Volatilite): Portföyün yıllık getirisinin standart sapması.
* Winning Day Ratio (Kazanan Gün Oranı): Portföydeki kazanan günlerin toplam gün sayısına oranıdır. Kazanan gün, portföyün değerinin arttığı günleri temsil eder.
* Sharpe Ratio: Portföyün fazladan alınan risk oranında elde ettiği getiriyi ölçen bir metriktir. Daha yüksek Sharpe oranı, daha iyi risk-getiri profilini gösterir.
* Calmar Ratio: Portföyün yıllık getirisinin maksimum çekilme (en kötü dönemdeki kayıp) oranına bölünmesiyle hesaplanan bir metriktir.
* Information Ratio: Portföyün fazladan alfa (piyasa üstü performans) üretme yeteneğini, alfa riski ile karşılaştırır.
* Stability (Kararlılık): Portföyün getirisinin istikrarını ölçer. Daha yüksek kararlılık, daha az dalgalanma ve daha güvenilir getiri demektir.
* Max Drawdown (Maksimum Çekilme): Portföyün başlangıç değerine kıyasla en büyük düşüş yüzdesidir.
* Sortino Ratio: Sharpe oranına benzer ancak yalnızca olumsuz getiri için standart sapmayı kullanır. Risk getiri profilini daha iyi değerlendirir.
* Skew: Portföy getirisinin olasılık dağılımının simetrisizliğini ölçer. Pozitif skew, olumlu ayrık getiri eğilimini gösterir.
* Kurtosis: Portföy getirisinin olasılık dağılımının kuyruklarının yüksekliğini ölçer. Yüksek kurtosis, aşırı olayların olasılığını artırabilir.
* Tail Ratio: Portföy getirisinin kuyruklarının genişliğini ve kurtosis ile ilişkisini ölçer.
* Common Sense Ratio: Yatırımcıların sıkça kullandığı teknikleri ve göstergeleri birleştirerek portföy performansını değerlendiren bir orandır.
* Daily Value at Risk (Günlük Risk Altında Tutulacak Değer): Bir gün içindeki maksimum potansiyel kaybı ölçen bir metrik.
* Alpha: Portföyün beklenen getirisinden bağımsız olarak, ekstra getiri sağlama yeteneğini ölçer.
* Beta: Piyasa endeksi ile portföyün hareketlerinin korelasyonunu ve piyasa üzerindeki duyarlılığını ölçer.

Getiriler grafiği:

![](/imgs/empyrial_getiriler.png)

Kümülatif getiriler ve benchmark karşılaştırması grafiği:

![](/imgs/empyrial_kumulatif_benchmark.png)

Yıl sonu getirileri ve benchmark karşılaştırması grafiği:

![](/imgs/empyrial_yil_sonu_getiri_benchmark.png)

Aylık getiriler ısı grafiği:

![](/imgs/empyrial_aylik_getiriler.png)

Çekilme grafiği:

![](/imgs/empyrial_underwater.png)

En kötü 5 çekilme dönemi grafiği:

![](/imgs/empyrial_en_kotu_bes_cekilme.png)

6 aylık kayan volatilite grafiği:

![](/imgs/empyrial_kayan_volatilite.png)

6 aylık kayan Sharpe grafiği:

![](/imgs/empyrial_kayan_sharpe.png)

6 ve 12 aylık benchmark'a göre kayan beta grafiği:

![](/imgs/empyrial_benchmark_kayan_beta.png)

Hisse senetlerinin ağırlıklarının grafiği:

![](/imgs/empyrial_agirliklar.png)

Paket ile beraber yapılacak başka bir güzellik "Calendar Rebalancing". Calendar Rebalancing, yatırım portföyünün belirli zaman aralıklarında (genellikle yıllık, altı aylık, üç aylık veya aylık) orijinal varlık dağılımına (ağırlıklarına) geri döndürülmesi işlemidir. Bu yöntem, portföydeki varlık ağırlıklarının zaman içinde farklı performanslar sergilemesi sonucu ortaya çıkan dağılım bozulmalarını düzeltmeyi amaçlar. Örneğin, eğer belirlenen stratejiye göre %50 hisse senedi ve %50 tahvil içeren bir portföy, hisse senedi performansının tahvillerden daha hızlı olduğu bir dönemde %60 hisse senedi ve %40 tahvil durumuna gelirse, rebalans işlemi ile portföy tekrar %50-%50 dağılıma getirilir.

```python
portfoy = Engine(
    start_date="2018-08-08",
    end_date="2023-07-29",
    portfolio=['AC.TO', 'CNR.TO', 'DOL.TO', 'ENB.TO', 'NA.TO', 'QSR.TO', 'RY.TO', 'SHOP.TO', 'T.TO', 'TD.TO'],
    weights=[0.1]*10,
    benchmark=["^GSPTSE"],
    rebalance="1y" # Diğerleri: 2y, 1y, 6m, quarterly ve monthly
)

empyrial(
    my_portfolio=portfoy,
    rf=0,
    confidence_value=0.95
)
```

Belirli bir risk seviyesi için en yüksek beklenen getiriyi veya belirli bir beklenen getiri seviyesi için en düşük riski sunan optimal portföylerin kümesi olan etkin sınır çalıştırılabilir.

```python
portfoy = Engine(
    start_date="2018-08-08",
    end_date="2023-07-29",
    portfolio=['AC.TO', 'CNR.TO', 'DOL.TO', 'ENB.TO', 'NA.TO', 'QSR.TO', 'RY.TO', 'SHOP.TO', 'T.TO', 'TD.TO'],
    weights=[0.1]*10,
    benchmark=["^GSPTSE"],
    optimizer="EF" # Efficient Frontier
)

empyrial(
    my_portfolio=portfoy,
    rf=0,
    confidence_value=0.95
)
```

Burada sadece hangi hisselerin seçildiğini ve bu hisselerin ağırlıklarını görelim.

![](/imgs/empyrial_etkin_sinir.png)

Ortalama-varyans analizi, beklenen getiri karşısında varyans olarak ifade edilen riski dengelemek için bir süreçtir. Yatırımcılar, farklı ödül seviyeleri karşılığında ne kadar risk almak istediklerini değerlendirirler. Ortalama-varyans analizi, yatırımcılara belirli bir risk düzeyinde en büyük ödülü bulmalarına olanak tanır.

```python
portfoy = Engine(
    start_date="2018-08-08",
    end_date="2023-07-29",
    portfolio=['AC.TO', 'CNR.TO', 'DOL.TO', 'ENB.TO', 'NA.TO', 'QSR.TO', 'RY.TO', 'SHOP.TO', 'T.TO', 'TD.TO'],
    weights=[0.1]*10,
    benchmark=["^GSPTSE"],
    optimizer="MEANVAR",
    max_vol=0.25
)

empyrial(
    my_portfolio=portfoy,
    rf=0,
    confidence_value=0.95
)
```

Burada sadece hangi hisselerin seçildiğini ve bu hisselerin ağırlıklarını görelim.

![](/imgs/empyrial_ortalama_varyans.png)

Hierarchical Risk Parity (HRP), portföy yönetiminde kullanılan bir risk yönetimi stratejisidir. Bu yöntem, portföydeki varlıkların riskine dayalı olarak ağırlıklarını belirlemek için bir hiyerarşi oluşturur. Amacı, portföydeki riski dengeli bir şekilde dağıtarak daha istikrarlı bir performans elde etmektir.

```python
portfoy = Engine(
    start_date="2018-08-08",
    end_date="2023-07-29",
    portfolio=['AC.TO', 'CNR.TO', 'DOL.TO', 'ENB.TO', 'NA.TO', 'QSR.TO', 'RY.TO', 'SHOP.TO', 'T.TO', 'TD.TO'],
    weights=[0.1]*10,
    benchmark=["^GSPTSE"],
    optimizer="HRP"
)

empyrial(
    my_portfolio=portfoy,
    rf=0,
    confidence_value=0.95
)
```

Burada sadece hangi hisselerin seçildiğini ve bu hisselerin ağırlıklarını görelim.

![](/imgs/empyrial_hiyerarsik.png)

Minimum varyans, bir portföyün en düşük riskle elde edilebilecek getiriyi ifade eden bir kavramdır.

```python
portfoy = Engine(
    start_date="2018-08-08",
    end_date="2023-07-29",
    portfolio=['AC.TO', 'CNR.TO', 'DOL.TO', 'ENB.TO', 'NA.TO', 'QSR.TO', 'RY.TO', 'SHOP.TO', 'T.TO', 'TD.TO'],
    weights=[0.1]*10,
    benchmark=["^GSPTSE"],
    optimizer="MINVAR"
)

empyrial(
    my_portfolio=portfoy,
    rf=0,
    confidence_value=0.95
)
```

Burada sadece hangi hisselerin seçildiğini ve bu hisselerin ağırlıklarını görelim.

![](/imgs/empyrial_minimum_varyans.png)

Kalan diğer birçok özelliğinin yanında son olarak rapor almayı da görelim. Hem .pdf formatında hem de .png formatında vermektedir.

```python
get_report(my_portfolio=portfoy)
```

![](/imgs//empyrial_rapor.PNG)