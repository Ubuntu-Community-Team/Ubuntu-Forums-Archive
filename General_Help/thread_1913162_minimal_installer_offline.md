---
title: "minimal installer offline"
date: 2012-01-22
forum: General Help
---

### Post by elliotn on 2012-01-22
is there a way I can install the minimal without working internet, I have the mini.ISO, is the a way I can get the require packages and put em un a flash drive then point the installer to it

---

### Post by davethewave83 on 2012-01-22
> **elliotn said:**
> is there a way I can install the minimal without working internet, I have the mini.ISO, is the a way I can get the require packages and put em un a flash drive then point the installer to it

it should be possible, you might have to install the base system first with the mini.ISO and then edit your /etc/apt/sources.list to include the usb device. I know you can include CD-ROM 

[http://wiki.debian.org/SourcesList](http://wiki.debian.org/SourcesList)

it says "You can use -d for the directory of the CD-ROM mount point or add a non-CD mount point (i.e. a USB keydrive)." but doesn't really explain how to do so with an example.

alternatively, after installation of the base system with the mini.ISO, you can copy the packages from your USB drive to /var/cache/apt/archives and then use ```
sudo dpkg -i /var/cache/apt/archives/*deb
``` to install them all. 

maybe you can find out how to add the USB to the sources.list though.

The packages can be download individually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but you should be careful and be sure to download the dependencies as well.


Alternative to downloading individually, you could install the packages on a machine connected to the internet, then copy the files from /var/cache/apt/archives to your USB, thus eliminating the need to download individual dependencies.

I'm not sure what the best way would be as I have never tried this but I wish you luck and success

---

