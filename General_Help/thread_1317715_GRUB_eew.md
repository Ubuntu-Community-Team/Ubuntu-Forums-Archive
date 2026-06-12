---
title: "GRUB eew"
date: 2009-11-07
forum: General Help
---

### Post by Twittery on 2009-11-07
What the f*** is wrong with Karmic . I tried it in my old PC and the first moment itself I felt it was buggy because after every boot up ( ie once after I plug in the PC) it takes me to some maintainance shell and asks me to run fsck , the problem gets fixed( after running fsck) and it occurs again  when I boot into it . I found that my computer had the problem that it cannot update  the time, BIOS time always goes back to Jan 1 2002 and Ubuntu at boot up finds that it is at future and therefore asks me to run fsck . Shucks ..

I also tried it in my new computer ( its just 3 months old) ,Ubuntu install and all other things went really nice but Grub beta 1.97 was the one creating the prob . I was running other 2 distros on the same host , but after Ubuntu install , when I tried to boot , them GRUB gave me an error which said ' to load the kernel first' . I was also not sure how to configure the new grub file (configuring old grub files were very easy) . I thought of doing the automated way ie running root (hd0,0) and then setting up GRUB
  from the grub cli but it gave the error , selected disk doesn't exist . ( I am sure that (hd0,0) is a boot partition though)
                                                    I tried booting from the live CD , for reinstalling the other distro ( I needed it badly) but even that didn't work and asked me to exit the installer ( I tried installing 3 times but no use.) Probably I had installed with the same CD for about 20 times on the same PC but this is the first time this has happened) . I was totally confused and tried booting from the HD but it the took me to GRUB rescue terminal and I am not sure what to do . Can't install and can't boot . What is wrong with this stupid GRUB . Help please !!!!!!!!!

---

### Post by sliketymo on 2009-11-07
Here is some good info on grub 2: 

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

