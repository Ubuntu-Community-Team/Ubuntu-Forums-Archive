---
title: "ubuntu 9.04,   	 System Halt Problem &lt;I/O error, dev sda, sector XX&gt;"
date: 2009-07-29
forum: General Help
---

### Post by xienohp on 2009-07-29
This problem annoys me much as its randomized feature makes works stop unexpectedly.
The problem has features like:
1) Except the mouse pointer and the application opened [tech. say, the application already loaded into the RAM], other procedures and processes are not available as soon as rebooting.
2) The harddisk accessing light is lighting continuously.
3) When entering the text mode, only a line of text would display:
End request : I/O error, dev sda, sector XX[XX is a ramdom numver]
4) This is a problem occured even in my old harddisk. My old harddisk has the similar features with the new one, except the old one gets WIN7 7227 together while the new one has only one OS,ubuntu 9.04, installed.
5) None of the business of the CPU speed, temperature and the RAM by my experience. Normally there is chance to halt when just login.

Hardware:
CPU : Intel P4HT dual core 3.0G
RAM : Kingston 2G + 512M 
harddisk :250G, brand? forgotton
OS 
Old:
partition1,50GB : Windows 7 7227 SP1
partition2,150GB : Old Windows Vista Ultimate[did't mark in bcdedit]
partition3,50GB+swap : ubuntu 9.04
New:
swap: ~2G
partition1,100GB: ubuntu 9.04
partition2,150GB: No OS, mounted.

e2fsck and fsck can denote the problem but cannot fix it.

Plz help me. I need your help for stable working. There is only a method now for stable working, live CD... Whatever what OS, the same proble exists......

---

### Post by xienohp on 2009-07-29
CAN SOMEBODY HELP ME?
I should add more informations:
the computer was brought 2 years before.
A OEM computer.
ubuntu-adjusted half year ago.
Nothing has been occured until weeks before.

---

### Post by blazemore on 2009-07-29
I found this was a problem with the NTFS partition when I had similar symptoms. Boot into Windows, and make it do a chkdsk, it will have to reboot, let it.

---

