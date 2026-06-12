---
title: "Problems running Live CD"
date: 2011-05-24
forum: General Help
---

### Post by humturtle39 on 2011-05-24
I have a Lubuntu 11.04 Live CD that I know is fine 'cause it boots on my laptop. Problem is, on my desktop, it stalls at this message: 



ata-id[182] : HDIO_GET_IDENTITY failed for '/dev/sr0'
ata-id[186] : HDIO_GET_IDENTITY failed for '/dev/sr0'

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system



Any ideas?

I don't actually know what model the PC is, which I know isn't helpful, but it's got an AMD Athlon XP 2400+ processor and 512MB RAM.

---

### Post by jerryjustly on 2011-05-24
I've never used Lubuntu, but when using Ubuntu I have sometimes stayed with the beta version, which seems just as good, because the final version won't boot.  So you might try downloading the beta.  Or if it's like Ubuntu, you can download an earlier version of Lubuntu, install it, and then upgrade to the newer version.

------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Try with the 10.10 version of Lubuntu and see if the issue reoccurs.  Sorry for the hassle.

---

### Post by BigD77 on 2011-05-24
> **linuxinstalledfromhdd said:**
> Try with the 10.10 version of Lubuntu and see if the issue reoccurs.  Sorry for the hassle.

How (or where) do you get the 10.10 version of Lubuntu?  Tried to google it, went to the website that was given, and the file is so small it couldn't possibly be a live disc or be able to load it.

I tried the latest (11.04).  It works Ok, except I can only really do one thing at a time.  If I am webstreaming a radio stations webside, Ok.  But when I try to record it with Audacity, nothing.  I checked with crtl-alt-del and found that the CPU was running at 100% while the memory was at 182 MB (I am running 512 MB of RAM.

HP XT919
Socket 370 Pentium III
512 MB of RAM

---

### Post by linuxinstalledfromhdd on 2011-05-24
Download Ubuntu  10.10.

Once you have it installed to your hard drive use:

From your terminal

sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install --no-install-recommends lubuntu-desktop

This will install Lubuntu.

For more information check out

[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp)

---

