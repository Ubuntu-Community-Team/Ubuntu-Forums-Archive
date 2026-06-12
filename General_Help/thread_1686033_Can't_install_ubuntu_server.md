---
title: "Can't install ubuntu server"
date: 2011-02-11
forum: General Help
---

### Post by ngbliss on 2011-02-11
I have a small network at home with one desktop and one notebook running Windows 7, one desktop running Ubuntu 10.04, a notebook running Windows XP, and a notebook running Ubuntu 10.10 all connected through a Cisco router. I had a x86 server running Ubuntu server 9x, and took the drive from it, and installed it in another box that also had an even larger drive.  I tried to install 10.04 and 10.10 both 32 bit and 64 bit versions of each.  Each one failed at some point in the installation.  I finally gave up and installed CentOS 5, which installed with no problems. However, I I couldn't get my windows machines to connect to it.

After a month of playing with CentOS, I decided to try Ubuntu again, and got new downloads of 10.04 64 bit, and 10.10 64 bit.  When I try to install 10.10 it gets to the 73% point in the installation and just stops.  I thought maybe it was just a slow point, but after several hours, I gave up.  When I tried 10.04 LTS, it gets to a point in the installation and then asks for the disk to inserted -

"Please insert the disk labeled: 'Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ Release amd64 (20100816.2)' in the drive '/cdrom/' and press enter. 

I'm at my wits end.  Any suggestions?

ngb

---

### Post by dcstar on 2011-02-12
> **ngbliss said:**
> 
..........
"Please insert the disk labeled: 'Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ Release amd64 (20100816.2)' in the drive '/cdrom/' and press enter. 


Try another CD/DVD drive, or if it is an IDE drive set it to Master on it's own cable.

---

### Post by sanmann on 2011-02-12
I have the same problem.

install from ide dvd....fail
install from sata dvd...fail
install from usb key....fail
install from usb dvd....fail

ubuntu server x64 9.04 there was no problem.

Im almost ...... :confused:

edit: :D:D:D:D

If you get "Incorrect CD-ROM detected" error on detection stage,
reboot, press F6 and then ESC to go to manual boot line editing, and add the option 'cdrom-detect/try-usb=true'.

On Ubuntu 9.10 server edition the install menu will be shown right after reboot.
Chose "Help" and then press F6.
At the boot prompt type "install cdrom-detect/try-usb=true" and hit enter.

---

### Post by cklaver on 2011-02-13
Hi,
I am facing similar problems. My USB stick is detected, and the first phase of the installation seem to be succesfull, but during loading components from 'cdrom', some point I get the message 
 
'There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, please check the integrity of your CD-ROM'
 
I guess this message should be interpreted as 'There was a problem reading data from the USB-stick ....'. Or could it mean that components read unto this point are correctly read from USB (through some link to USB) but that there is one package with a hard path to cd-rom?
 
Does anybody have experience in this?
 
Thanks 
 
CK

---

### Post by cklaver on 2011-02-13
Oops, found it. I tried to install a 64 bit version on 32 bit hardware. Everything seems to go OK for a while, until you hit the above message.

---

### Post by CharlesA on 2011-02-13
Make sure you verify the MD5SUM or SHA1SUM of the ISO before burning it to cd.

---

