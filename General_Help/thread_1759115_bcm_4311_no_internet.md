---
title: "bcm 4311 no internet"
date: 2011-05-15
forum: General Help
---

### Post by jjj123 on 2011-05-15
Hello everyone, I made the jump from windows to ubuntu, and must say it has been rewarding for the most part, with a major learning curve, and would like to say thank you in advance for any help, that you can give me, I upgraded from 10.10 to 11.04, and wish that I had not done this, for it has been nothing but problems, I have a hp laptop dual core 64 bit with the broadcom bcm 4311 wireless card, with no internet, I have tried everything in the posts that people have had success on and nothing seems to work, it finds my wireless connection, and connects, without internet. I do not want to go back to windows, but I have been without internet on my notebook for several days now, can someone please help me figure out what needs to be done, maybe I am just not going through the steps, the sta driver lists my card, and have tried the bcm43 x 64 installer but nothing works......please help

---

### Post by dino99 on 2011-05-15
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by jjj123 on 2011-05-15
urce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  libdesktop-agnostic-fdo-glib fortune-mod libdesktop-agnostic-vfs-gio
  libdesktop-agnostic-cfg-gconf librecode0 fortunes-min
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:4311)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
whzz@whzz-HP-Pavilion-dv6500-Notebook-PC:~$

---

