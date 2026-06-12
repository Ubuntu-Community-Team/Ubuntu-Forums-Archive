---
title: "grub dual-boot help"
date: 2010-08-28
forum: General Help
---

### Post by zosky on 2010-08-28
hi yall. in in kubuntu 99% percent of the time, but i still like to drop to winBlows every so often to get my frag on. my setup was aces till my KVM died and the new one isn't playing nice... 

MY SETUP: 
```
/dev/sda  = grub-legacy (GNU GRUB 0.97) in MBR
/dev/sda1 = root - Kubuntu Lucid
/dev/sda2 = /home
/dev/sdb1 = /media/storage (non-bootable)
/dev/sdc  = grub-legacy (in MBR)
/dev/sdc1 = root (ubuntu Jaunty mini + xbmc-stand-alone)
/dev/sdc2 = winBlows XP

```
THE SITUATION: (far from a clean solution, i know, but) i was using the bios boot-selector to pick sdc & then XP ... the new KVM wont let me, so i can only get to grub on sda

$cat (sda1)/boot/menu.lst has
```
title Windows NT/2000/XP (loader)
root (hd2,0)
chainloader +1
savedefault
makeactive

```

THE RESULT: "starting up..." and nothing happens ???

any suggestions please

---

