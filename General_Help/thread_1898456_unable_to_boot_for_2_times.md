---
title: "unable to boot for 2 times"
date: 2011-12-21
forum: General Help
---

### Post by sirvinniei on 2011-12-21
hi,

today I tried to boot up my pc it said something about unable to mount cryptswap then it looked like it was gonna boot (black screen) but instead it turned back to the lines of boot text with the last line bein starting ASLA timidity

the I tried to boot it a second time,
this time it something about having to check sda 5 (my ubuntu partition) because it has been mounted 38 times without checking it (this may be a wrong translation) "this may take a few minutes"
then it did the same thing as the first time i tried to boot: it looked like it was gonna boot but turned back to the boot sentences instead with the same last line as my first boot

The third time I tried to boot I booted succesfully but I stil get the feeling my PC is messed up and I dont want this happening again

sincerely, Vince

---

### Post by BC59 on 2011-12-21
Boot from a Live Cd and execute this command:

```
sudo fdisk -l 
```

The -l is a lowercase L

---

### Post by sirvinniei on 2011-12-21
> **BC59 said:**
> Boot from a Live Cd and execute this command:

```
sudo fdisk -l 
```The -l is a lowercase L
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x00092aa8

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *        2048   973995852   486996902+   7  HPFS/NTFS/exFAT
/dev/sda2       973996030  1953523711   489763841    5  uitgebreid
/dev/sda5       973996032  1947762687   486883328   83  Linux
/dev/sda6      1947764736  1953523711     2879488   82  Linux wisselgeheugen

Schijf /dev/sdb: 3965 MB, 3965190144 bytes
49 koppen, 48 sectoren/spoor, 3292 cilinders, totaal 7744512 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x00000000

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1            8192     7744511     3868160    b  W95 FAT32

Schijf /dev/mapper/cryptswap1: 2948 MB, 2948595712 bytes
255 koppen, 63 sectoren/spoor, 358 cilinders, totaal 5758976 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x6778e920

Schijf /dev/mapper/cryptswap1 bevat geen geldige partitietabel

```

translation:
```
Disk / dev / sda: 1000.2 GB, 1000204886016 bytes
 255 heads, 63 sectors / track, 121601 cylinders, total 1953525168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector Size (logischl / physical): 512 bytes / 512 bytes
 in-/uitvoergrootte (minimum / maximum): 512 bytes / 512 bytes
 Disk ID: 0x00092aa8

  Device Boot Start End Blocks Id System
 / dev/sda1 * 2048 973995852 486996902 + 7 HPFS / NTFS / exFAT
 / dev/sda2 973,996,030 489,763,841 1,953,523,711 5 extended
 / dev/sda5 973,996,032 486,883,328 1,947,762,687 83 Linux
 / dev/sda6 2879488 1947764736 1953523711 82 Linux swap partition

 Disk / dev / sdb: 3965 MB, 3965190144 bytes
 49 heads, 48 sectors / track, 3292 cylinders, total 7744512 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector Size (logischl / physical): 512 bytes / 512 bytes
 in-/uitvoergrootte (minimum / maximum): 512 bytes / 512 bytes
 Disk ID: 0x00000000

  Device Boot Start End Blocks Id System
 / dev/sdb1 7744511 8192 3868160 b W95 FAT32

 Disk / dev/mapper/cryptswap1: 2948 MB, 2948595712 bytes
 255 heads, 63 sectors / track, 358 cylinders, total 5758976 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector Size (logischl / physical): 512 bytes / 512 bytes
 in-/uitvoergrootte (minimum / maximum): 512 bytes / 512 bytes
 Disk ID: 0x6778e920

 Disk / dev/mapper/cryptswap1 no valid partition table
```

---

### Post by BC59 on 2011-12-21
Did you remove 2 partitions from the middle of the disc creating others?

---

### Post by sirvinniei on 2011-12-21
> **BC59 said:**
> Did you remove 2 partitions from the middle of the disc creating others?
I don know,
but the installation of Ubuntu went really badly and I did mess up my partitions

---

### Post by BC59 on 2011-12-21
The message > Disk / dev/mapper/cryptswap1 no valid partition table it's a bug and there is no solution, or at least an easy one. Try to use your system like this and in the future and when you are tired of the problem, try to reinstall Ubuntu or whatever other system, but deleting and creating new Linux partitions.

---

### Post by sirvinniei on 2011-12-21
> **BC59 said:**
> The message  it's a bug and there is no solution, or at least an easy one. Try to use your system like this and in the future and when you are tired of the problem, try to reinstall Ubuntu or whatever other system, but deleting and creating new Linux partitions.
thanks,
1 remaining question:
I know I should always backup data but I don have the hardware to do so (don't have much important data either so it doesn matter much)
But is it possible to delete reinstall ubuntu without touching my personal folders?

---

### Post by BC59 on 2011-12-21
You should do it in the future. You have to make 3 logical partitions for Ubuntu/Linux:
1. The system ( **/** ) about 12-15GB
2. The swap about equal to your RAM installed
3. The rest of the space dedicated to **/home** (inside are the folders Documents, Videos etc).

This way you could reinstall the system formatting the **/** but leaving intact the **/home**, on which you will have your personal data.

---

