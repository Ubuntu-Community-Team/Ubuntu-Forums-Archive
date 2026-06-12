---
title: "i need torestore windows after ubuntu 11.04 instalation"
date: 2011-05-01
forum: General Help
---

### Post by petex on 2011-05-01
Hi I installed ubuntu 11.04 on my system. To do that i needed to remove partition with old windows XP (which did not work banyway but i belive it hold startup files for entire system) becasue i already had to many aprtitons on the drive. Ubuntu was installed on logical partitin. The strange thing is it looks like systems starts from sda even thoug it's installed on SDB

I still have windows7 partition but there's no way to start the windows from it. Fixing via windows recovery disk did no good and i would hate to get reinstall as i have crucial dfate on this drive 

here's my sudo fdisk -l


Dysk /dev/sda: 120.0 GB, bajtów: 120034123776
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 14593
Jednostka = cylindrów, czyli 16065 * 512 = 8225280 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0xa0e7a0e7

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sda1   *        2504        9876    59223622+   7  HPFS/NTFS
/dev/sda2            9877       14593    37889272    f  W95 Rozsz. (LBA)
/dev/sda5            9877       14593    37889271    7  HPFS/NTFS

Dysk /dev/sdb: 500.1 GB, bajtów: 500106780160
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 60801
Jednostka = cylindrów, czyli 16065 * 512 = 8225280 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0x000c794c

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sdb1   *           1        8463    67979016    7  HPFS/NTFS
/dev/sdb2           54253       60802    52600833    5  Rozszerzona
/dev/sdb3           14840       22973    65334872+   7  HPFS/NTFS
/dev/sdb4           22974       49231   210917385    7  HPFS/NTFS
/dev/sdb5           54253       60173    47552512   83  Linux
/dev/sdb6           60173       60802     5047296   82  Linux swap / Solaris

Wpisy w tablicy partycji nie s&#261; w tej kolejno&#347;ci, co na dysku

Dysk /dev/dm-0: 5168 MB, bajtów: 5168431104
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 628
Jednostka = cylindrów, czyli 16065 * 512 = 8225280 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0xf9c4e40e

Dysk /dev/dm-0 nie zawiera poprawnej tablicy partycji (i.e. does not contain correct partition table)

---

