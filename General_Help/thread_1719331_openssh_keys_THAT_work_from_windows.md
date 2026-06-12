---
title: "openssh keys THAT work from windows ????"
date: 2011-04-01
forum: General Help
---

### Post by highspider on 2011-04-01
How do I make a ssh-key pair that work with windows 
  (its at office I have to use windoz) ;(

Using win Putty- [COLOR=SeaGreen]would use something else if i knew it worked and free.[/COLOR]

Every ssh-keygen I make with Ubuntu ends up a  [COLOR=Red]"AES-128-CBC"[/COLOR]

```

-----BEGIN DSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: [COLOR=Red]AES-128-CBC[/COLOR],376BD0CBE24B107C09BA3355520C92DB
.
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: [COLOR=Red]AES-128-CBC[/COLOR],17DB65DFA5960C5AAC5BDABF0A30FC97

```putty only works with ciper [COLOR=Red]DES-EDE3-CDC[/COLOR]

Didn't ask this question with out tiring in vain the internet searches and old post.
even tried manual edit of a putty-key to -> .pub  --> authorized_keys

---

### Post by CharlesA on 2011-04-01
You can convert the keys created with ssh-keygen to keys putty can use by using putty-gen.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by highspider on 2011-04-01
> **CharlesA said:**
> You can convert the keys created with ssh-keygen to keys putty can use by using putty-gen.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")

yes but only if the keys created with ubuntu ssh-key gen are [COLOR=Red]DES-EDE3-CDC
 [COLOR=Black]and mine are allways[COLOR=Red] [COLOR=Black]end up [/COLOR]AES-128-CBC. [COLOR=Black]

I don't know how to make a [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Red]DES-EDE3-CDC[/COLOR] [COLOR=Black]in ubuntu.[/COLOR]](*,)
[COLOR=Red][COLOR=Black]     
-------message box------
[PuTTgen Error]
[X]  [Couldn't load private key(ciphers other than [/COLOR][/COLOR][COLOR=Red]DES-EDE3-CDC[COLOR=Black] not supported)]
-------end message box-----


  [/COLOR][/COLOR]

---

### Post by CharlesA on 2011-04-01
Hrm. What key are you trying to convert?

IIRC, you need to convert the private key (id_rsa) not the public key (id_rsa.pub).

---

### Post by highspider on 2011-04-01
This one "yes I will make new after I get it work"
```

-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: [COLOR=Red]AES-128-CBC[/COLOR],17DB65DFA5960C5AAC5BDABF0A30FC97

SjcH1nA/uDDrLWuO4ADwWwGtvq5CqzP7wGeEhkQtyX5JHRxqL422plXUqnvBeVNr
QrNBhBsydVqxXuaNqdyVnKR+14TOm5a31yOKLIwRHb+cANJMqg4BdcWb1J9grlhk
wJWohnF1eCur13DMN4cMJiqvPjaSOaWIfZXS93s5exAL7Abq+g/GWal8K/cf1DYW
9WDu7LJyZAKRgOl6D045HbqxTfysbyzOMjuy/RmPcd++EoTUnO5evs0MKA9ohMJR
UN1VLl/WeK4bTRYdBbIC+TgE84qLBfwDdFRnsyUTR7+Qvn/AEzzsFKsUj1raZexO
OgMPvsPHl5UjJZx9qp8xeALBdDuam13y2orIc27NUYquj3RNsLqHR5trB3M0qov8
rU18Hgc2QaPMWvkV/4ZrPniS8C6Y8VL9jBU5jqiWah5WKW3sTi9VLLF9+FVPNoJn
C+2SzTYY0bqy6vgalHfRyRDxq5JpBIP87xVwt1oBtq/uF/kAkoiRZUFVIdxtqWyF
RJ9gOqTBPdLGozlZjTejh+AFakK2TQmYQ4NcJHrMyEQi7ekhUhDKZmCq38sP3v2e
q9N1zQb2fw+2cKl80ov9PlEWBZBmNvHQdjXfmlFUB0wmBvfki+Gzt9wQbF+StjPW
5r9lpgUL3UElGNcrRroXeQdKSiKAyE/U/In9vKO0ylPp8s1WoRYQo9czWSRXIGAg
y0GkUzJRcLqgzrQBOygNey733oL0Y2iqAUqh6HIcbEOHKliSyXNKBh1GANPFhBWn
Hx6l4zUmONVljzX8uLWqo3NvABm9J30F9Q+05wILzY1+zrOJC6uSMkMXxifHLbxz
cI3EIHB7iF1u05D6q/g7nbdlWFVtYKhnn2Iev+FHFlYGxBTsZ0S00sj6icIf4Qhe
8Y9YaF7EQHa9oUZn+jZ1jEzA20kk0D3G98GpvlmAvcsMZ+5Bmr1xD1E8AjVp5QxM
3IZ6hv8iqg+PQo4lnuXZcHR80gehL3M1ThppCv2B+4vk/5BdDVqyn8o77Z1b7f72
upHBeRqg/uA1RpFSZaPsyVon55gl54OhEEpWlnGwbHyeMwUiIAmMM1NbXPeK+Byx
F0FNfrSA3B6u4I46yLg6x99IXW/xxieu2l6krSIkX9aWlhf3oYu5DJ6Bi8KW5RTN
tVy1sRce/HPjcRSa5/usbi8xHFCFKD9H/OYAyfLj/S1JAW2BZ8lYd35CtDdcuFB5
cY2csnRcQDVBRprcOTJcBioh+mCtwd3n4IFOasz6zxhNTLJhmSx+iAH06vdU13mX
X5xVhZ5fgy6qvnO8QD5pxs3IctEdhbkhv16aezVpnPVGZVd3moSX84muG/s8N5BB
GTvf7HqTzaF+mp1igaNncfoj5tFgQfjzUaT9mAESzGXb6qWOJttWPIO2va716Ww7
SCPA7vIPeW+nnPTXyUE4Z6/0KqsV2rq3ylv9Ud0ZPTzUeZzzgy7bZ3sxP7gK1w2s
v8UyfG1RCRJELV+F1H6M/8Qi66mJ8EA6XJLjWCVoaoavNSTN2E6zByU+OauNynqO
M8iaNIXjCWxDeOtG0mwJ7Oc/LoDkYOoXy1dYncXSDeR0/Npb0GFgdIsvrM+VlIAJ
-----END RSA PRIVATE KEY-----

```

---

### Post by jerome1232 on 2011-04-01
Those should work just fine, mine are AES-128-CBC and I have successfully converted them to putty keys using puttygen.

---

### Post by CharlesA on 2011-04-01
How are you generating the keypair?

I just used this (no switches):

```
ssh-keygen
```

It created this:

```
-----BEGIN RSA PRIVATE KEY-----
MIIEoQIBAAKCAQEAuYgFApp0Gv10OtGRm/Xt9HEBk9e4rAXT310WiIzEA/dWUSZd
6G6iBkGxRruAJ6f16yWxF7dRvBFMKUPZHSbRweFfDEnUHflBJNw+XlrRWD6Y9s86
PytGiFH5RVCvBRcnS65N6oquerZVHYRpC4LIBn9Mcg/9MrSMZUwTV/SbBMluPxnP
7m609mAkS1EVdLbNsWWhGuGZgl6ARYRNckI9dx09hDp9cPeI2qq8LZaoN7R/nWSl
/N6fFL1wzd22RLgeWSDvAJ4A4w4ikG3Nw8rbH0uZXbFl//brCmnXVClyIQyT8DX4
/ssKSjNOS5dTdKE647M85JXynF/JGgCX+UwVNwIBIwKCAQBkt42w9MKvkOdTIU8L
hYEs7OOZZnoxf4GlI+epNnkJd6Pi6PEmZ/GOXi0JI/Uc14V/pr84wpoVov11fJpu
6TAKKeMj7ZBoCvd6aO6oP+38tERouaNG3PpnQnFgJHxEl4pcSK30WemwVFoXVoIq
0feOf56HD/56nIa6paQZze3AxDAcV8QxSbN2v9gJLvz+hoPdSE3XqAKZfEqte0Fm
SufT1KCN1zyQCVXfWkPqxUEqv0NyLNR4OUAUf5ptG8c6kPLKE2p9WgQi3U8kPelc
JwEArgya9BxbtgOUj1IMOA7A3UVCnbopCydKkxLtDC1BJQwiPcfG2yS196gZBvw+
CpELAoGBAPcQTm2K1HM9dV1z9YLbaLL+cme0HJwHbXH0bpYmQAk2PNampIEE0UxK
7S7mN/FordVa4YH87CbrwfrJ/Olt7I585514qLScE7QE8H9PcMpWA/eLswvHTAXt
UthPiE2Q57NHbCISN1nkhDI4SwCS9v9PsFiQpUtnxcohQKCAGrJBAoGBAMA989CP
i8E8e+gJzx7fY8l5o+1gPqfZd+MRg4IxQlNO33UAuKfOm8bL4WECr/tlVX7b+qoV
AkV8fDEf8P+F23/GS3JrJw7DYsHPdwxeztkLZVS0jYRMW5smX9OqwJ2YqDinVnKG
BeFIGXJ5lDVpqVsfClle47RsIqDlmCbRAvl3AoGAHDxgvA/dxAcGGU8Uvn95rg5z
eZDtU6kT0oJVyARfFv7iYaylFg8t3NVc72rEkJ4/wJysDtsTrK06vZNtXIGXYL3R
U9NGewqF6LAbfEOX3JwdteQUdl/rbmRD+3bNv7jKBdxG31KJ+6UWbCOwzN2YkjT+
NgHnAU2wNFuSW3xa0osCgYAV+HOizpOhDjoL490oGYe/QRoMgAcpICr1YRZYBaEu
F6SCZnuA5GmTD/yAHZB0gJwOf4pclK/NbVAFnUAdM96SQoxHlzep6nGvv/BZL2gY
zho1kPo7AWmOEwOjKXUZU0Zs3+yfX8YoYALoguxd4DCcsxcgKBoF/brQj0SWuM0j
0wKBgQDgqGJUzgffGFcsuUnhCxp1oJOGQlC0PtxB1HwSMX63pA8B5sN+XPHmidcP
HDz0J5ZhaAMifF85skzEvs87+7/iymcxDkXQiMZ1FaHLS5jo31f6KzE5qHlEwPle
Oz2JWIGirFQnirvEz8jh8dQb5i3sJEthU0WvxvAnhtcxvkENfg==
-----END RSA PRIVATE KEY-----

```

---

### Post by jerome1232 on 2011-04-01
Add a passphrase to it, and it will look like his.

---

### Post by CharlesA on 2011-04-01
> **jerome1232 said:**
> Add a passphrase to it, and it will look like his.
Ah hah! Thanks.

---

### Post by highspider on 2011-04-01
What am I doing wrong?

Ever time I try convert putty-gen.exe gives the same error.
   Couldn't load private key (ciphers other than DES-EDE3-CBC not supported)

step by step
```

gmi@Server:~/.ssh$ [COLOR=Red]ssh-keygen[/COLOR]
Generating public/private rsa key pair.
Enter file in which to save the key (/home/gmi/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/gmi/.ssh/id_rsa.
Your public key has been saved in /home/gmi/.ssh/id_rsa.pub.
The key fingerprint is:
xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx gmi@Server
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|     .           |
|      E .        |
|     o o =       |
|      * S =      |
|       @ B .     |
|      * B . .    |
|       + o o     |
|          .      |
+-----------------+
gmi@Server:~/.ssh$[COLOR=Red] cat id_rsa[/COLOR]
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-128-CBC,36AE32742D9246E16D5DD14D5B381C78

RI0n8Jvj7mKBSpKjBmIxOwldz+eica6baiA5lgxAil3DGUQxpQJ5JlzS29ZInV70
zL+8sEIfrHZCf55UjytNrtXjD3veF9QzF0fsTGcw40xkII5is+bAsH88dOZqhG4j
iCyyZfA9TNZR4bBmnkShnPPON1r2jQaQ+Vr+NnfUtHh8+brW+AiIbXy5FfbvBhOq
Zh6wc5MpcF3OwqG2zRROnKs9Z5pngRAXgCWd4daqDvT/COKxhPWXwxkzfrx2PPHV
oRnoYEqosG15g2cxnt2y8AvyYbd2HqLHyWm0vJMBELj70Zaz8Dr5XNJbvz8Dvo1q
ZdLYWgWAbzzVMjId7OJUZRcy+2u5Ny4efVmjj22XUTQvcvJfjlx5WLAh1keGJI76
fUQhXgQhlTxjXXhhcBkdM/ZdPKijkk/DWjcZm1CXJRSwhaZzwumV8Sl4zBHYSnrA
865EmDYvpM2ugCZr9f0VpVfpQtCLrba+oySiF6nXMLVbRbeH+sBoaFZjJBH1p9Vg
ejoUASYTpQ5AHa7SS/VVXPK48bBGDZDCO+Ot8zjOTMVjAjCCDd5n3O+A0SZnxlO1
R2Zsd7SwtRN+GyLHUpeeO467IB0uIgh3vyt1hgnQQka3D+X1InF44J0dgTo26xe7
3dKJP+6caDN8Nhzuo78PqnkrU9EdyOc4sG/XDOhhTRKIkprDSz3eKud58W9SMEnE
2V4t0muY6W8p+ZNFtd5HcFda67bPSiRphFkaPtiDmwyx7oglpm+GA/t1aENxRl6X
uW9BX19609yNZV1ykHTv8DT0+UpWfq1VO164GCwc7lERMDq05M/8n/AF7sLQaaNB
KB8bt6hq/n540j+fn2kL/0c81aeftV6ud69qZy+uRxeu7DBJyKb3PHUGm7XIL24j
OU1nAlXY1FOGTmckE47cDqLbmLVMf+zF0wPq0CpVHAR14y1nHCmBX0wouVFWPC6I
SVY/Y2K4EHOyfdOCKZLv+pW8HAVDWbQ4diPbA2VggRxJWIEDWu6E2EFnBUE2kyS9
R0NmU/+4N+U6x17GN9aOfXoFb10ZpQ66Pnr9DwF3KtEswszLCsRIjhyqd9SzrmOH
0cYQs4uYKo+25h4AdnN+K0QPqxfkTnrWMzzTM3JM59QmMbsigGY7g2z0xwYUnZ1p
NmwIX/bKvhn2HJKnN5fNBuw96abNYrOn/0YO1GpbUXBYdvmE5BnY942IDD5AFRGp
nymvsLIIF1Jzb8vpTK6kjofwN9AyJMioWbyMaJ/U/U5CK6QQyFPkGegVGQLowgfO
VH9I3CiWOMepqbD6EZUEedUxosI1OxDHjUpke+UfHPpPv8H/bwVHoVrT56EDHtBa
X3gJX8GhObvtj9b87RyWh6DIpHdEGrkp7aIT8Njpohnvtx76UFQqa+v90uJkuYzt
uUGZNFGrjMxGJ3kkv4wpERuPceo3JSnLBrEI1zTBuLhNd3YDRp9QnmfsXeJ266HM
Pq0/tXj+JScwxQstayLN33QWlmiQ6a3btAxT1P2qNjAqDJzRLfGuqe0+yUQkjiZr
mXJBbg4xcx0XdX4uH23X6oU0GbUIZjrorxKjgZ5ENjOgcimGpQQKXAuK7MY1L8FK
-----END RSA PRIVATE KEY-----

```then windows 
```

C:\>pscp -P 22 gmi@192.168.0.104:/home/gmi/.ssh/id_rsa id_rsa
gmi@192.168.0.104's password:
id_rsa                    | 1 kB |   1.7 kB/s | ETA: 00:00:00 | 100%
[COLOR=Lime]
<---then-->[/COLOR]
[COLOR=Red]puttygen.exe[/COLOR]
  conversions --> import key --> c:\id_rsa
ERROR!!!

```[ERROR]
[COLOR=Red]  see screen shot[/COLOR] error.bmp
  note: id_rsa renamed to id_rsa.txt for upload

---

### Post by CharlesA on 2011-04-01
Are you clicking on "load" or Conversions > Import key ?

EDIT: Nevermind, I tried converting the key and it gave me the same error.

EDIT2: I created a key the same way you did, but it's using a different encryption:

```

charles@Thor:~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/charles/.ssh/id_rsa):
/home/charles/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/charles/.ssh/id_rsa.
Your public key has been saved in /home/charles/.ssh/id_rsa.pub.
The key fingerprint is:
dc:b5:52:64:b0:03:0e:80:2b:69:62:71:13:b1:a1:9c charles@Thor
The key's randomart image is:
+--[ RSA 2048]----+
|   =+.. . ..o    |
|..+oo  o . +     |
| Eoo.   . o o    |
|+o.    . . + .   |
|+.      S o .    |
|           .     |
|                 |
|                 |
|                 |
+-----------------+
charles@Thor:~$ cat .ssh/id_rsa
[COLOR="Blue"]-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,BC3CF1FD5DD68720[/COLOR]

lvR6a5AIQSc+WB/WEfnwJeiirLn/wPSRXpQ3W03vlJ5PG3V1G/oUW9L/k7NfYtMj
UJeqo9LKXPnrlNhufzd+sY41jZW4uKXcx381XhaotnGEgF12aOZXR0vUJqqkfOhW
uZs9q7MwaAWqHz/yO/MedPU6cG5nU1hy693+PC6HO6Ol2JAxtV2jjDPt0E0rxnlt
fhjmiwmKA5dE7LaGK/LYCH6tCIm21ar/iFntQHB+RZefpWFpHmZiFboPGH44Rg2C
OwdXJfwmBRtMHxQ2EJGxOo9THAoEnLDsx3crl98BTSGQXJf0P6KdyzT7CxB3ghQ8
dQicDOKnWM5qQrLG8uO7ToSSXa9ietbuZvnazPrAGGLWS/SBcCpLFLRQRcdg8aAZ
ODmpixXSflVlM9Ittw49xY0U8bjiWX9AO+P8MrCxl3fCesRFe+okOikpWboqzpZC
zdgDarsw2tPR7WjSD8Tusb6ARSA6cFkMjODQSe7xX3L4MTadkcju9o9iOE7q3D4p
BczpXRT2FqSi98W286t+nFypOzoQghqGTQQ2Z3oRgR1mB/Pak1QH9YvFasn4UJim
bL208Sr4doZmj9pPD1txrbQblc7CqoKWXyAJ9JS7CFvCtL+NfBhlJkvKe9kRYaef
gQsxwshRbjVQ7nyFZqcPh32fAycshvoCqgUzvTRk1fbg5jZLgwIhoPUU0edjbR1L
6O945FQDFSqfSMqEb0kHA+rDgT8JzkQA0gfLkyWMmNh/fIqqKwUmkLqtDBQJDt0C
k281kkw/d0UGqAe2P1Qh5mDqybiSAD+DzXVNFIcppWOGJK+v1e9s5CrXBokXqmpk
YpIqbvyd4zZ6FtAisAJX09tUNRGDv3t2RjJ252XgEc5eTivweQBW+gM57qJ28yql
cw7iay/RXUWYAdZ81LLD2v5sz8fKvpv+x9uAQtfiM3I3sAL4pYJoDe970ZIrHSnc
CyO1yh8pDq9zumK+isK48oHMB4NfVSz0agZGc9cQTk0yUsajmNIzwctuS5EAIDzD
yGXdS8K1vBaEL3v8IL1VBVicXnnpo8a+aMRBcZyhu9xGm4no1xHCIer7X1GLblwr
QscnAwFoNLXrHPX+CEDTrsISXem8G/DRlZVW3jsAeIft+lamF3o1zgh3u8Y6G2hp
1FjGfMAw8wRvE0NdOFlYYIPOjlsQV2zsYdDigxnxs5QLkslM1a7zT+st1ebY7PXV
K7HWTXccvjvmbX/uVNF7HFRSZjc0mItTfNcDb36UnNjkrl6Keci9PRgIapa34gt4
lnydTPVvhhz3CBCDfdt+17rSEPbikick6q/jjaVXwMeO0D3N2l/IZgnJsqsZcZ5I
BfJktMuwWRGeXN7MCRaklYfJlVHeYPgwXQggzH3LT258R96+tFdh6bja6PASj/W5
u8XLoFS/rGO2qzJwRIliMvnLROIqB0PpN/oc1P4yIKjLB0xuDVYctailG/zWB+QP
4fD9LZpAg1I8pIKUr4DGr5sfpWZhFzNACJKk744FfFsuf6XZipIzKhS6a3UEEYfW
Cw+SpLO9sAsjxHUmQMeBRQhz3upr+kUcsVeZiU8InittiG+3ntJrcA==
-----END RSA PRIVATE KEY-----

```

---

### Post by jerome1232 on 2011-04-01
Well for me his key is working, I just don't know the passphrase obviously to actually open it.

See Screenshots of PuTTy-Gen for the results of importing both mine and highspider's key.




Me generating a key

```
ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/jeremy/.ssh/id_rsa):
/home/jeremy/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/jeremy/.ssh/id_rsa.
Your public key has been saved in /home/jeremy/.ssh/id_rsa.pub.
The key fingerprint is:
52:a8:f2:d7:5f:0a:af:94:d9:17:1a:36:26:09:db:11 jeremy@voiceserv
The key's randomart image is:
+--[ RSA 2048]----+
|        E        |
|       . .       |
|      o o        |
|     . = o       |
|  . . o S = .    |
|   o   o B + .   |
|    . . * o o    |
|     . . + +     |
|        ..+      |
+-----------------+

```

This is what it looks like

```

-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-128-CBC,39B204B941BDB09147AFA14E66ACA7FE

9bKwW/u/szJU5tA0ptOGXXYLZOOvlIZXry1AoXVkYMfghLSEX6LCxxx4EJrPutmS
CgGv+uVlWeeretDujeP7DVFJRuMQ9oKVZ3WoV8JoTEC8osukr+6ku08KIn2iiVnJ
fC4RlGk16fm0KdZPMz4jTasxL9wjUjPCIWkjqspw2CURMLYqEwFnzImk1+wl5YHv
Ve7JJaolXKrK010vnYNvJ31MkoZijoJ9T2L3GS9e61c2MOzlwd8n2Pka4Zq5bqGl
tQHDsM7ccYWY+LTmjybbIw/DfPO2DBqo8g48XafbX/Ah+TLHkrVkeNcLJoXcxy9T
QuoXN78xzIr6haHESD1JTPY7aYLnP+hpRSFD8/LEtR6uenDzYnlwsqCVFU/F8OTz
hxlafxB4FtU6bnT9JPJNqvnKvceHM6WQ9hY+VID1aJDZuS3D0cm6OVooOrky2Ywu
6XvZE7GmuXNS/LwOaYLrxJXdeRUPc9ZNcFlPbxTK1skjAWZ7yeRbZUN2cKzgKIGp
Jp4+DPMr+071+0Ba/s+x/SY1vKGM/CBp7eNNZIpSrTSllwepmnOlng9Q/P7qWAx7
PhXVAncRXFwipvwZKWist5xtW/tY6ch2chnG6LCYe1NL6wdw+7CSEAetL9cv9Tc0
M+z3MAW1LKC2wwI6cBaVRdbUy2feR5IV76SZXLmZJB6c1LZTzNX8JeIDvjhdGm2Y
wjjMg4dLFVDZi7A47JpGgiw3n5sRKDku2lG73Bc9jd4MXNoe6GRFeBVFu476jiRN
fvJ0NTsR65yRXQf3Mq13LwvGE4+mn0n/muf7HA0JDRR+cNwRc2Te6cDPve26dQEq
NxckmBN0lmIt9fdkJDomcQnv6w8X7eg0Q2+JTbxsan7VPCdndeG97ZvMyUf220hf
rRVeJxUj40k33CNzuPmWFkCcWF3Vmhy8NK9wl8IG+2mJ/PuyRPgPRnPTWsOK0C9x
dwc0Zu3L/dbUKWKW16V6WqttUiSOK4R9RUVFdwzOq40hLwMpSvRPOYbLtf5mypbx
Y9DjPIbu9wR/rUBddiie/IkVL86asq59YUyrsOQJSagqCtyQw4aBUT+g4OlO8iDc
3jeqqUNAC1ukiWmrWcUeMmn62VB60q8Zu16nCsW5vw2VJeVBSe+u49hzPXCM1l77
gpd6BYSR+7uTO2nmCfxW8vReXSdullhWYlZIuFZAktmJTD26jEogANzfqSApp006
ZMFypj3GeMlZiH4Rem7bWyUXTN4iVNyZ+ge/TQVXyS4ksx+fzGYryHULCL5LmWU3
CD+FDSxsXMRVcZA0RLS3kPC2fQ9+yO+kEgv9tQ3h0/NByw2PQO+NfmSn8Fiui9JB
rTpCWZdEv7IDdvSYUx0B9cR0ZGDaZxKusC8FGPqQHCdpi6vF7UlApvQsKweKT+6U
Z5p9D2qEYiv1yc49XVcNH6ZsqLjthOLsowst0KV05iPccuebH8xx5yr/ZKC/2cZs
62+RlJLKUB7L9Ke7hdKsTYfeRCoHBDWwAU8WC3EqTfOdW9SHiUurm4vbTrsHyJpY
oBBtokILAJQNBDb+adWzBex45iw0f78sC572+WbkRGuen1Zkkmb6+1r7o2Ks40ft
-----END RSA PRIVATE KEY-----

```




So my question is what version of ssh-keygen and PuTTy are you guys using?

My PuTTy-Gen says Development Snapshot 2010-07-04:r8970

I'm using Openssh (couldn't see a way from a quick glance at man page to get ssh-keygen's version)
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010

---

### Post by highspider on 2011-04-01
> **jerome1232 said:**
> 

So my question is what version of ssh-keygen and PuTTy are you guys using?

My PuTTy-Gen says Development Snapshot 2010-07-04:r8970


sorry for delay LOL your post where on page2 I keep reloading page1


PuTTYgen
Release 0.60.0.0
1997-2007 Simon Tatham. All rights
    reserved.

I will try your version and reply the results

---

### Post by jerome1232 on 2011-04-01
In case your having trouble finding it, (actually this one is newer than mine but whatever it should work)

[It is here!]("http://tartarus.org/~simon/putty-snapshots/x86/puttygen.exe")

---

### Post by CharlesA on 2011-04-01
> **jerome1232 said:**
> In case your having trouble finding it, (actually this one is newer than mine but whatever it should work)

[It is here!]("http://tartarus.org/~simon/putty-snapshots/x86/puttygen.exe")
Ah, newer version. That explains it.

Mine was version 0.60

I was using the version of ssh-keygen found in Lucid.

---

### Post by jerome1232 on 2011-04-01
Lucid is 10.10 right? I wonder why your getting DEC while highspider and I are getting AES.


edit: I'm going to take a second to laugh at myself, right next to my portrait it says 10.10 Maverick Meerkat.


doh, so the default must have switched between versions.

---

### Post by highspider on 2011-04-01
> **jerome1232 said:**
> In case your having trouble finding it, (actually this one is newer than mine but whatever it should work)

[It is here!]("http://tartarus.org/%7Esimon/putty-snapshots/x86/puttygen.exe")
   In case .... Yeapers Was having trouble. works
 

[:guitar:jerome1232]("http://ubuntuforums.org/member.php?u=453029") :guitar:


jerome1232 and CharlesA[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=923868")[U][B]
      [/B][/U]thank you

---

### Post by CharlesA on 2011-04-01
> **jerome1232 said:**
> Lucid is 10.10 right? I wonder why your getting DEC while highspider and I are getting AES.


edit: I'm going to take a second to laugh at myself, right next to my portrait it says 10.10 Maverick Meerkat.


doh, so the default must have switched between versions.

Lucid is 10.04. :)

---

### Post by highspider on 2011-04-01
My home PC Maverick 10.10 --  So IDK if default crypt changed on normal Maverick
   This is the Ubuntu server 10.10 (where all these question came from)
```

gmi@Server:~$ [COLOR=Red]uname -a[/COLOR]
Linux Server 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux
gmi@Server:~$ [COLOR=Red]dpkg -l | grep openssh[/COLOR]
ii  openssh-client                            1:5.5p1-4ubuntu4                  secure shell (SSH) client, for  secu                                     re access to remote machines
ii  openssh-server                            1:5.5p1-4ubuntu4                  secure shell (SSH) server, for  secu                                     re access from remote machines
gmi@Server:~$gmi@Server:~$[COLOR=Red] cat /etc/issue[/COLOR]
Ubuntu 10.10 \n \l


```

---

