---
title: "Boot Error Problems 9.04"
date: 2009-10-12
forum: General Help
---

### Post by tosh0_11 on 2009-10-12
Hi,
 
I installed Ubuntu V 9.04 on an old PC last week. Everything seemed to go well ... i was able to access internet through DHCP connection and download several updates.
 
Some days later when i again booted up the system I got a sequence of error messages beginning as follows 
 
[FONT=Calibri][SIZE=2]32.8160301 ata2.00: exception Emask 0x0 S act 0x0 Sact 0x0 SErr ox0 action 0x6 frozen[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]and ending with :[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]73.8163031 ata2.00 status : drdy[/SIZE][/FONT]
 
The system will eventually boot but I cant go online ... there is a red x over the networking icon. 
 
The same situation applies when I boot directly from the live cd.
 
I am completely new to linux and would appreciate help to resolve this issue.

---

### Post by QIII on 2009-10-12
I would suggest two things:

1.  Please don't take this wrong, but could you check the physical connections?  I only ask because I have dogs that like to chase tennis balls under the desk and kids that like to check out the neato cable thingies and cool blinking green light dealies. ;)

2.  Run memtest from the LiveCD to rule memory issues out on the error messages.  An old PC may just be getting, well, old.  Hardware eventually fails.  If it is memory, I hope it is not so old that you have to pay an exorbitant price to replace it.

---

