---
title: "grub problem: Unrecognized option '/dev/sda1'"
date: 2010-08-09
forum: General Help
---

### Post by dvdwd on 2010-08-09
I can't seem to get Grub installed.

```
sudo fdisk -l
```returns:
/dev/sda1   *           1       37528   301438976   83  Linux
/dev/sda2           37528       38914    11129857    5  Laajennettu
/dev/sda5           37528       38914    11129856   82  Linux-sivutus / Solaris

I tried:
```
mount /dev/sda1 /mnt

```And then:
```
grub-install --recheck --root-directory=/mnt /dev/sda

```but it returns:
Unrecognized option `/dev/sda1'

What's the problem?

---

