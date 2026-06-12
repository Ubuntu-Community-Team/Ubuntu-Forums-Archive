---
title: "Dual boot - windows xp on HD and ubuntu on EXTERNAL HD"
date: 2010-07-11
forum: General Help
---

### Post by vamanu9 on 2010-07-11
Hi, I installed Ubuntu on external USB hard drive and while booting I did got option to log into windows XP, Ubuntu. Both operating systems ran fine. i.e. GRUB had overwritten MBR and I was able to dual boot. 
Main issue: I have installed Ubuntu in external hard-drive so that I can use Linux whenever I want other people who are using same computer can operate on WindowsXP. Sometimes my external hard drive gives problem if there is loose connection and so that oper people using computer do not face any problem I want to disconnect external USB HD whenever I am not using Linux. 
GRUB menu was pointing to external hardrive so disconnecting it meant my system wont boot!!
I rewrote MBR using WindowsXP CD recovery mode. Now I am unable to boot from external USB hard disk( I thought I would be able to if I choose USB hard drive in BIOS option but it did not work it logged into WindowsXP by default).
Is there any way I can change WindowsXP boot.ini file so that it also shows Ubuntu in external hard disk? Or is there any way.(I do not want GRUB way as then I would have to keep my external drive connected to log into windows - which I do not want).
Thanks for reading this long message :) I got tired writing it ;-) hopefully some geek here would be able to solve problem.

---

### Post by Mark Phelps on 2010-07-11
You would need to install GRUB2 to your external drive so you can boot from it.

See the link below about reinstalling GRUB2 from an Ubuntu LiveCD (Section 11):

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Make sure you mount your external drive, not your internal drive.

---

