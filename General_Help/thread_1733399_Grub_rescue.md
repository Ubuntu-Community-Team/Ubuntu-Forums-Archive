---
title: "Grub rescue"
date: 2011-04-19
forum: General Help
---

### Post by Pat2ick on 2011-04-19
Hey there. I just recently decided to install Ubuntu alongside windows 7 64bit. I was working fine until i decided to increase the partition size of the unused space to take up some space of an unused partition i had made earlier. When i tried to reboot windows I got the error - 

error: unknown fileystem. 
grub rescue> 

I have tried a windows repair disc with no reults, it cannot find any problem with the startup routine and i have looked at many different tutorials and information about how to restore grub using command from the grub rescue menu. It's all jut going over my head a bit and would appreciate any help, thanks.

ubuntu 10.10

---

### Post by Pat2ick on 2011-04-19
I've managed to get as far a showing the grub menu but when i try to run windows from there it just returns back to grub again. Quite lost as to what to do now.

---

### Post by kiyop on 2011-04-19
I wonder if you by mistake installed grub(2) on PBR of Windows partition.

Boot with Ubuntu live CD or Ubuntu installed in internal HDD if possible and run boot info script
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and paste the result between [ code] and [/code] in "Reply" and submit.

---

