---
title: "win7 on raid0, ubuntu on 80gb, add windows to grub2"
date: 2010-03-22
forum: General Help
---

### Post by keytthom on 2010-03-22
Hey, I have windows 7 on a raid0 array, and ubuntu 9.1 on 80gb sata drive, but when I try to boot into win7 from grub 2, I get the error: invalid signature, does anybody know how to successfully add win7 to grub2, or ubuntu to windows boot manager.

---

### Post by keytthom on 2010-04-28
bump.

anyone??

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
From ubuntu open bash and type ```
sudo update-grub
``` That should get you going.

---

### Post by toilety on 2010-05-14
I had same problem with keytthom,
I have windows7 on my raid0 configuration with 2*250G hard drive and ubuntu 9.10 on sata drive.

I installed windows7 first and then ubuntu. And when I select windows7 from grub menu 
I got the same message as keytthom. I followed Sin@Sin-Sacrifice's method but didn't worked.

I found solution from else where and i wish this might help you too.
when grub menu appears move to windows7 and press 'e'.
then add following code line above 'chainloader +1'
     set root=(hd0,1)

---

