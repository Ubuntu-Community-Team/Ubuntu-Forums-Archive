---
title: "Can't get into ubuntu"
date: 2009-08-07
forum: General Help
---

### Post by infiniah on 2009-08-07
Originally I had Ubuntu installed as the only operating system and now since Windows 7 was relesased I wanted to give it a try. 
Now that Windows 7 is installed, on the second half of the drive (it was split...) GRUB is gone and I don't know how to get it back so I can boot into both operating systems, instead of just W7.
So... how do I get Ubuntu back..

---

### Post by Mrandersonjr on 2009-08-07
Im sorry but you have to reinstall,windows 7 does not play nice with ubuntu. It rewrites to the MBR,

---

### Post by furuno on 2009-08-07
Check [this article]("http://https://help.ubuntu.com/community/WindowsDualBoot"), specifically the [Recovering GRUB after reinstalling Windows]("https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows") part...

---

### Post by harry2006 on 2009-08-07
> **infiniah said:**
> Originally I had Ubuntu installed as the only operating system and now since Windows 7 was relesased I wanted to give it a try. 
Now that Windows 7 is installed, on the second half of the drive (it was split...) GRUB is gone and I don't know how to get it back so I can boot into both operating systems, instead of just W7.
So... how do I get Ubuntu back..
as you said only the GRUB got missed, i guess W7 apparently has overwritten the MBR and hence you are not able to get back to Ubuntu. One simple solution would be to pop a live ubuntu cd and ask it to boot from hd, as i remember that way it will be able to detect all OS sitting on that disk even if the entry is missing from MBR. 
this might help:
[http://www.astahost.com/info.php/restoring-grub-boot-loader_t14048.html](http://www.astahost.com/info.php/restoring-grub-boot-loader_t14048.html)

---

### Post by infiniah on 2009-08-07
Alright thanks for the replys

---

