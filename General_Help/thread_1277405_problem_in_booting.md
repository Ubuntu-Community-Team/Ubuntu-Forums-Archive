---
title: "problem in booting"
date: 2009-09-28
forum: General Help
---

### Post by hesseny2000 on 2009-09-28
i have a problem in my Pc 
after installing Ubuntu 9.4 desktop and enjoy withit 
yestarday wgen try open my pc 
ubuntu cant compet booting and i see screen 
[B]
kINIT:NO resume image .doing normal boot
mount:mountig /dev/disk/by -uuid /770cdc71-fa4d-469c-babf-60822fe1594a on root
failed:ivvalid argument[SIZE=2] 
mount:mountin /dev on /root/dev faield no such faile or dirctory[/SIZE]
[SIZE=2] 
mount:mountin /dev on /sys/dev sys faield no such faile or dirctory[/SIZE]
[SIZE=2] 
mount:mountin /dev on /proc /proc faield no such faile or dirctory[/SIZE]
no init found system dosent HAVE /abia /init 
no init found try passing init = bootarg
Basybox V1.10.2 (ubuntu  1:1:10 2-2ubunut7)built-in shell(ash) .
Enter  help  for a list of built -in commands.
(initramfs).

plz helpme wat can i do 
[/B]

---

### Post by Diabolis on 2009-09-28
Your PC is not finding the hard drive. Did you installed it in a external hard drive, unplugged it and plugged it again? or something like that? You must connect the drives in the same order in which they were when you installed Ubuntu.

---

### Post by Darkwing-Duck on 2009-09-29
Another way to do it is to fix your MBR (Main Boot Record) from a live CD and restore GRUB from there. 

Follow this and see if it helps!

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by hesseny2000 on 2009-09-30
[SIZE=6][COLOR=teal]**thanks for all **[/COLOR][/SIZE]
[SIZE=6][COLOR=teal]**try now and returne**[/COLOR][/SIZE]

---

### Post by hesseny2000 on 2009-09-30
[CENTER][SIZE=5][COLOR=Blue]well. don,t know what  I can say??
many thanks for all friends
problem is fixed 
[/COLOR][/SIZE][/CENTER]

---

