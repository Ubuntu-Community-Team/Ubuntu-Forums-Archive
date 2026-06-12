---
title: "how to boot to ubuntu after reinstalling windows (not recovering the grub)- read plz"
date: 2010-02-15
forum: General Help
---

### Post by spaik on 2010-02-15
hi

so i installed ubuntu on windows a while a go and it was working fine. but i had problems with windows so i formatted the windows partition and i was wondering if there is a way i can recover ubuntu and make boot again.

i'm running windows 7
the ubuntu is installed on another partition.

please help me

and thanks ;)

---

### Post by Megafag on 2010-02-15
> **spaik said:**
> hi

so i installed ubuntu on windows a while a go and it was working fine. but i had problems with windows so i formatted the windows partition and i was wondering if there is a way i can recover ubuntu and make boot again.

i'm running windows 7
the ubuntu is installed on another partition.

please help me

and thanks ;)

Why not just recover the grub? i am pretty sure that is the best way to make your ubuntu bootable again...

---

### Post by oldfred on 2010-02-15
So we can see your exact configuration from a liveCD download and run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by bodhi.zazen on 2010-02-15
You can either configure the windows boot loader to boot Ubuntu or you can install grub to your MBR or you can make a grub boot disk, floppy or CD.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by boosterjet on 2010-02-15
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
Worked for me.

---

