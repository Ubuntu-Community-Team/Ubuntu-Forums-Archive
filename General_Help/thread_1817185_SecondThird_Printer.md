---
title: "Second/Third Printer"
date: 2011-08-03
forum: General Help
---

### Post by _jeremy_ on 2011-08-03
Brand spanking new user here. I'm running 11.04 desktop. I have three identical printers attached via usb. I was able to add one via the normal method (accessories/printers/add works, as does the web interface) and it works perfect -- but I can't figure out how to get the other two to be accessible. They do show up with lsusb.

Bus 001 Device 004: ID 04e8:3297 Samsung Electronics Co., Ltd
Bus 001 Device 003: ID 04e8:3297 Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 04e8:3297 Samsung Electronics Co., Ltd

Is there a trick?

Thanks for helping a newb.


Jeremy

---

### Post by _jeremy_ on 2011-08-03
post removed. that guess was all wrong.

---

### Post by _jeremy_ on 2011-08-03
this post removed. invalid info.

---

### Post by _jeremy_ on 2011-08-03
Here's what I've tried that doesn't wok. I've got it to where now the jobs just sit in queue. "Processing"

[FONT="Courier New"]user@pc:~$ ls /dev/usb
lp0  lp1  lp2
user@pc:~$ sudo lpadmin -pSamsung_1 -v /dev/usb/lp0
[sudo] password for user: ************
user@pc:~$ sudo lpadmin -pSamsung_2 -v /dev/usb/lp1
user@pc:~$ sudo lpadmin -pSamsung_3 -v /dev/usb/lp2
user@pc:~$ lpr -PSamsung_1 filename.ps
user@pc:~$ lpr -PSamsung_2 filename.ps
user@pc:~$ lpr -PSamsung_3 filename.ps
user@pc:~$[/FONT]

---

### Post by _jeremy_ on 2011-08-04
So... no one out there has run into this I guess?


Jeremy

---

### Post by _jeremy_ on 2011-08-04
For anyone interested, the solution was to disable usblp, then add each printer to CUPS the normal way.

---

