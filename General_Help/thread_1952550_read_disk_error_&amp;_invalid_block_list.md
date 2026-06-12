---
title: "read disk error &amp; invalid block list"
date: 2012-04-04
forum: General Help
---

### Post by svennson on 2012-04-04
Hello,

I have a Dual boot (Windows 7 + Ubuntu 12.04 LTS) 
I updated my Ubuntu recently and it worked nice. However this evening I booted and Windows 7 gave me a "Read disk error, press ctrl - alt - delete to reboot" (infinite) and just after GRUB I get a "fout : invalid block list"

I was able to mount my windows partition from within ubuntu, I also tried to use the windows install CD but it couldn't not recognize my HDD (it could before) and therefore not repair it. Anyone have an idea how to fix it w/o breaking windows cry baby ?

sudo fdisk -l 
```
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0xe3a05b96

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *        2048   293571809   146784881   83  Linux
/dev/sdb2       293572608   293777407      102400    7  HPFS/NTFS/exFAT
/dev/sdb3       293777408   449196031    77709312    7  HPFS/NTFS/exFAT
/dev/sdb4       449209530   488392064    19591267+   7  HPFS/NTFS/exFAT

```

This was the result of boot-repair :
[http://paste.ubuntu.com/914880/](http://paste.ubuntu.com/914880/)

---

### Post by svennson on 2012-04-04
I'm sorry, this can be marked as fixed, I ran another boot-repair and this seemed to fix the problem. So it was GRUB who was having some issues.

---

### Post by dcstar on 2012-04-05
> **svennson said:**
> **I'm sorry, this can be marked as fixed**

Then why don't **you** do it?

---

