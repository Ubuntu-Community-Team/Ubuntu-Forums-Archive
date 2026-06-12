---
title: "no print"
date: 2010-12-25
forum: General Help
---

### Post by hani270 on 2010-12-25
hello

we have workgroup network in the home, and the printer "hp laserjet p1005"  connected at the server (OS : windows server 2003) and I am connected to the Internet by the server without problems.

but when i want to print any file, it remains in (processing) and no print.
it's picture for this problem :
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179320&stc=1&d=1293271989[/IMG]

sorry for bad english!

---

### Post by dino99 on 2010-12-25
looks like it cant find the lp path: install xpp, it might help

found this issue:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/372407](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/372407)

maybe something to check there

---

### Post by hani270 on 2010-12-25
i have installed xxp, but nothing is new.
i am beginner and your answer is not clear.

thanks dino.

---

### Post by dino99 on 2010-12-25
what is the output of:

sudo gedit /etc/modules

other question:
is your system having only 1 lp or several (maybe lp0 is wrong, try lp1, or else, check your devices)

another silly question:
is your printer ready to print ? (power on, paper ok, cartrige ok, no standby, etc)

---

### Post by hani270 on 2010-12-25
this is "/etc/modules" content :

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


i have one printer, and when i change lp0 to lp1, i see "not connected" !!
(my printer is ready)..

---

### Post by dino99 on 2010-12-25
ok go ahead:

is foo2zjs is installed (might be: sudo apt-get install foo2zjs)

then run:

cat /usr/share/foo2zjs/firmware/sihp1005.dl > /dev/usb/lp0

[http://www.openprinting.org/printer/HP/HP-LaserJet_1005](http://www.openprinting.org/printer/HP/HP-LaserJet_1005)

---

### Post by hani270 on 2010-12-25
> 
root@han-desktop:~# sudo apt-get install foo2zjs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
foo2zjs is already the newest version.
The following package was automatically installed and is no longer required:
  openssh-server
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 163 not upgraded.
root@han-desktop:~# cat /usr/share/foo2zjs/firmware/sihp1005.dl >  /dev/usb/lp0
bash: /dev/usb/lp0: No such file or directory
root@han-desktop:~# cat /usr/share/foo2zjs/firmware/sihp1005.dl >  /dev/lp0
bash: /dev/lp0: Device or resource busy
root@han-desktop:~# cat /usr/share/foo2zjs/firmware/sihp1005.dl >  /dev/lp1
cat: /usr/share/foo2zjs/firmware/sihp1005.dl: No such file or directory


:(

---

### Post by hani270 on 2010-12-28
Help !!

---

### Post by hani270 on 2011-01-06
Help !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by ianmillington on 2011-01-06
I may be off target here but doesn't the location parellel:/dev/lp0 signify a printer that is connected directly to your computers parallel port rather than via a network? I would suggest you remove it, then go through the add printer wizard and select a networked printer. 

It may also help if you check on one of your other machines as to how they describe the location of the printer. It may comprise a location (eg your network name/location) or an IP address. 

HTH

---

