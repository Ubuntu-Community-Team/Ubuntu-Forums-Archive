---
title: "Installation of Windows 7"
date: 2009-08-14
forum: General Help
---

### Post by GreggyZed on 2009-08-14
Hi,

I'm a fully converted Ubuntu user, it is my primary OS and I love it so.  However, as a CS student, I have access to the MSDNAA and as such have access to a free copy of Windows 7.  I'm currently downloading it now.  

Here's my issue: 

I have Windows XP and Ubuntu on one hard disk, and plan to install Windows 7 on a second hard disk.  Is this possible?  And if so, how does one go about setting up GRUB to have XP, Ubuntu, and Windows 7?  I know similar issues have been raised, but I tend to get frightened when guides aren't exactly what I'm trying.

I imagine that the idea would be to restore GRUB, but would it automatically include all the other OSes? And if not, would I add them in the file like this?:

title Your New Operating System&#8217;s Name
root (hd0,0)
makeactive
chainloader +1

Thanks in advance.

---

### Post by GreggyZed on 2009-08-14
Okay, everything has gone fine in the Windows 7 installation and have added Windows 7 to the bootloader.  However, when I select Windows 7, I receive the following error:

Selected cylinder exceeds maximum supported by BIOS

It sounds like there's no way around this, but I'm hoping somebody will be able to tell me.

Thanks again!

---

### Post by P4man on 2009-08-14
Maybe this helps:

[http://wiki.linuxquestions.org/wiki/GRUB#Error_18_on_Dual_Boot_Systems_Using_a_Single_Hard_Drive](http://wiki.linuxquestions.org/wiki/GRUB#Error_18_on_Dual_Boot_Systems_Using_a_Single_Hard_Drive)

---

### Post by GreggyZed on 2009-08-15
Hey, thanks for the link.  It got me on the right track and I solved things from a different tract.  I installed GRUB to the partition that has Linux and reinstalled the Windows 7 bootloader to the MBR.  I then used EasyBCD in Windows 7 to add a boot entry to the Linux partition and then GRUB loads from there.  

So this is another problem solved!

---

