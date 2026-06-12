---
title: "SAMBA without CDROM?"
date: 2006-05-05
forum: General Help
---

### Post by aparsons on 2006-05-05
I have a SFF pc and just took out the CDROM to make room for a second Harddrive.  How can I install SAMBA without a CDROM?  ubuntu is already installed, I just need to install Samba...

[FONT="Courier New"]= = = = = = = = = = = = = = = = = =
root@apkcfs1:/home/aparsons# sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcupsys2-gnutls10 libkrb53 samba-common
Suggested packages:
  krb5-doc krb5-user samba-doc
The following NEW packages will be installed:
  libcupsys2-gnutls10 libkrb53 samba samba-common
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/4706kB of archives.
After unpacking 11.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter
= = = = = = = = = = = = = = = = = =[/FONT]

---

### Post by JoshHendo on 2006-05-05
sudo apt-get install samba

---

### Post by IYY on 2006-05-05
Edit your /etc/apt/sources.list file (sudo nano /etc/apt/sources.list) and comment out (by placing a # at the beginning of those lines) the lines that mention a CD-ROM.

---

