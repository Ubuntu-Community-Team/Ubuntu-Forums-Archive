---
title: "Iphone wont mount"
date: 2010-12-04
forum: General Help
---

### Post by hiphopapotmas on 2010-12-04
I really want to use my iphone in ubuntu, but it will not mount. I recently installed libmobiledevice, ideviceinstaller, and sbmanager. I followed the steps from this page : [www.uluga.ubuntuforums.org/showthread.php?p=9351196](www.uluga.ubuntuforums.org/showthread.php?p=9351196)
everything seemed to go well with the install, but my iphone never shows up on the desktop.
when i try this in the terminal:
$ ideviceinfo
i get the following

GNUTLS ERROR: A TLS fatal alert has been received.

also when i type this into a terminal:
lsusb | grep Apple
my output is
Bus 002 Device 003: ID 05ac:1294 Apple, Inc. iPhone 3GS
please help me

EDIT: my external hard drives mount automatically and my iphone works fine with my hackintosh netbook. this is very important to me so any help is greatly appreciated

---

### Post by hiphopapotmas on 2010-12-04
bump

---

### Post by Spyderkid on 2010-12-04
you don't need to bump it after an hour do it after a day I would of thought


Go to system > administration > User and Groups > Advanced settings > User Privileges, and tick all the boxes

---

### Post by hiphopapotmas on 2010-12-04
> **Spyderkid said:**
> you don't need to bump it after an hour do it after a day I would of thought


Go to system > administration > User and Groups > Advanced settings > User Privileges, and tick all the boxes

That didnt work. i know that ubuntu knows its there because of the usb command output, but i dont know how to get tit to mount

---

### Post by hiphopapotmas on 2010-12-05
> **hiphopapotmas said:**
> I really want to use my iphone in ubuntu, but it will not mount. I recently installed libmobiledevice, ideviceinstaller, and sbmanager. I followed the steps from this page : [www.uluga.ubuntuforums.org/showthread.php?p=9351196](www.uluga.ubuntuforums.org/showthread.php?p=9351196)
everything seemed to go well with the install, but my iphone never shows up on the desktop.
when i try this in the terminal:
$ ideviceinfo
i get the following

GNUTLS ERROR: A TLS fatal alert has been received.

also when i type this into a terminal:
lsusb | grep Apple
my output is
Bus 002 Device 003: ID 05ac:1294 Apple, Inc. iPhone 3GS
please help me

EDIT: my external hard drives mount automatically and my iphone works fine with my hackintosh netbook. this is very important to me so any help is greatly appreciated
a

---

### Post by jozef.kutej on 2011-02-25
I had to do:

`sudo apt-get install libimobiledevice1`

to make the ifuse mount.

---

### Post by jozef.kutej on 2011-02-25
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=609928](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=609928)

---

### Post by toiletgoose on 2011-06-02
Here is what I did (running Mint 10, but would assume it would be the same for everything):

Downloaded the latest libmobiledevice from here: [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

- Extract the files
- Run ./configure in the directory, find what installs and dev packages you are missing to compile the library.
- Downloaded all the tools required in ubuntu to build the package.
- Downloaded all the -dev packages required to build the package (libglib2.0-dev for example).
- Once built, ran a sudo make
- Ran sudo make install > install.txt. Then searched the install.txt to find out where it was installed. If I were clever and new more about building packages I would have specified where to dump the final product.
- Took the library from /usr/local/lib (libimobiledevice.so.1.0.5) and copied it to /usr/lib
- Removed the soft link for libimobiledevice.so.1, linked to libimobiledevice.so.1.0.1 and instead linked it to libimobiledevice.so.1.0.5.
- Ran an ifuse --root -o allow_other /media/ipod and all was well again.

Worked for me... have an iPod Touch 2G running iOS 4.2.

** Note: I did not install the .deb package or tried to remove the old one because it would have removed a bunch of other stuff with it. Just installed it in tandem with the older .deb package.

---

