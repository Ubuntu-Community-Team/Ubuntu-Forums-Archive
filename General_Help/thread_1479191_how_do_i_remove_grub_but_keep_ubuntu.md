---
title: "how do i remove grub but keep ubuntu?"
date: 2010-05-10
forum: General Help
---

### Post by young hastings on 2010-05-10
when i start my pc i get the windows boot manager and i select whatever. when i pick ubuntu it then brings me to grub and i have to pick again, this was annoying but i didnt mind but now grub is broken and wokr work anymore so i cant load ubuntu at all. 

I was fine usin ubuntu 9.10 (i didnt bother with the 10.04 cos it wouldnt work last time i tried to upgrade) but i decided to install ubuntu studio so it seemed everything installed ok but now when i reboot grub gives me some big message about typing in codes n stuff and i dont have a clue. ive tried my best to fix it with replacing the wubildr file like the guide i found said but it didnt fix it.
but if i get rid of grub i wont have to worry about it anymore and ill be able to get back to business
how do i do it? all guides ive found only say how to remove it after ubuntu is gone

---

### Post by cbecker78 on 2010-05-10
Grub is needed to boot ubuntu, you simply can't get by without it and still boot into your linux os... unless you install a different boot client.  But it will be the same thing.  Your best bet is to reinstall grub...  The method to use will depend if you have grub legacy, or grub2.  I think if you installed 9.1 as a fresh install, you will probably have grub2 (you'll want to verify, but I think that is right), and if you upgraded from 9.04 you will have grub legacy unless you specifically upgraded/installed the newer grub at some point.

Once you have grub working again, you can always set it to boot directly into your default OS without displaying the menu, if that is what you want.

---

