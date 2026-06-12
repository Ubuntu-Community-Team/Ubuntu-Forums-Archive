---
title: "Guide to triple booting?"
date: 2009-12-07
forum: General Help
---

### Post by bittiez on 2009-12-07
Hey guys, I just got ubuntu 9.10 installed! Right now I am dual booting Windows 7 and Ubuntu. I want to know if I can add xp to my list? I have around 25gb of un partitioned space, I just want to know if I install xp on it, will everything work fine?

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
Yeah but you'll have to restore grub after you install XP because the Windows MBR will overwrite it. Google can help you with that if you need.

---

### Post by bittiez on 2009-12-07
Alright, thank you very much :)

---

### Post by bittiez on 2009-12-07
Hey guys, I have a problem.

I first had windows 7 installed, then installed ubuntu, and now I just installed XP, and I used the livecd to get grub going again, but all that i have listed is Windows 7 and Ubuntu..

I also looked at a guide on adding it manually to menu.lst but when I open that to edit it, its completely blank

---

### Post by bumanie on 2009-12-07
You need to put the windows bootloaders together. A good tool to do this with is easybcd bootloader available from [here]("http://neosmart.net/dl.php?id=1"). After using easybcd, essentially if you choose win7, it should then give the choice of booting win7 or xp. Not sure if you will have reinstall grub again or not - I have done this in the past, but have always got the two windows partitions booting properly before installing linux - so it is something you will have to find out by trying.

---

### Post by ranch hand on 2009-12-07
You are not going to find your /boot/grub/menu.lst because you are using grub2.

As I understand it the MS boot loader should, when you chainload to it, give all the MS options.  I do not know if that is true of XP.

You may want to do what ever it is you do to fix the MS MBR making sure that you use the Vista boot loader.

Then use these directions for recovering grub2;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the file editing instructions, you will need to run "update-grub" and "grub-install /dev/<your drive>".

If this doesn't work run this script and post the results here;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

