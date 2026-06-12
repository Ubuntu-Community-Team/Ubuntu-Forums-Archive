---
title: "OMG please help"
date: 2010-09-06
forum: General Help
---

### Post by mslina on 2010-09-06
[SIZE=4]i installed ubuntu 10.04 LTS and everything seemed to be going great the installation went through completely until it said that i need to restart for the installation to be complete and start my new software. 

The problem is I clicked restart and it did its thing with all the partition stuff coming up and the CD popped out and these errors came up and been on the computer for the last 5 minutes which reads [ 1630 . 428395 ] end_request :   I/0  error , dev  sr0 , sector 502544 
all the way down the screen please tell me im not completely F@^! ed
[/SIZE]

---

### Post by sgosnell on 2010-09-06
Restart it again.  If that doesn't work, you can always reinstall from scratch.  It's hard to tell from your sketchy description exactly what is going on, but it shouldn't be fatal.

---

### Post by Rubi1200 on 2010-09-06
As sgosnell already pointed out, you are not being very verbose here.
We need to know things like the computer specs. (RAM, graphics, drive capacity etc.), if you have other operating systems installed and what, your level of experience with the command line.
The more you tell us (if you think it is relevant), the better we can help.
Thanks.

---

### Post by philinux on 2010-09-06
> **mslina said:**
> [SIZE=4]i installed ubuntu 10.04 LTS and everything seemed to be going great the installation went through completely until it said that i need to restart for the installation to be complete and start my new software. 

The problem is I clicked restart and it did its thing with all the partition stuff coming up and the CD popped out and these errors came up and been on the computer for the last 5 minutes which reads [ 1630 . 428395 ] end_request :   I/0  error , dev  sr0 , sector 502544 
all the way down the screen please tell me im not completely F@^! ed
[/SIZE]

Remove cd and reboot.

---

### Post by The Cog on 2010-09-06
That just happened to me, installing 10.10 beta. sr0 is a cdrom driver, so it's basically telling you that it can't read the cd rom any more - hardly surprising since it's just been ejected. 

As others say, just reboot and you should be fine.

---

