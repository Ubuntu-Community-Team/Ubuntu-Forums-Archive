---
title: "Need Help With Public Key"
date: 2009-10-15
forum: General Help
---

### Post by ram2008 on 2009-10-15
[SIZE="3"]I'm trying to get the public key for Sun Microsystems' Virtualbox to work.  I've added the necessary line to repositories but can't get Synaptic Package Manager to accept the public key.  Tried doing it at the command level in a terminal with *sudo apt-key add sun-vbox.asc* but when I do that, I get the message "gpg: no valid OpenPGP data found."  I must be missing something.  Here's an excerp from the Sun Microsystem page:


Debian-based Linux distributions ¶

Add one of the following lines according to your distribution to your /etc/apt/sources.list:

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) dapper non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) etch non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) sarge non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xandros4.0-xn non-free

The Sun public key for apt-secure can be downloaded here. You can add this key with

sudo apt-key add sun_vbox.asc

or combine downloading and registering:

wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -

The key fingerprint is

AF45 1228 01DA D613 29EF  9570 DCF9 F87B 6DFB CBAE
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

To install VirtualBox, do

apt-get install virtualbox-3.0

Any suggestions as to what I'm doing wrong?  I'm running Ubuntu 9.04.[/SIZE]

---

### Post by wilee-nilee on 2009-10-15
Did you copy and paste the wget into a terminal and run it. The key is only to confirm that your getting the files from the correct repositories and updates as well.

---

### Post by BenAshton24 on 2009-10-15
All you need to do to add the key is run this:
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

---

