---
title: "iso image"
date: 2011-03-24
forum: General Help
---

### Post by nesdunk on 2011-03-24
I have been told to download "ubuntu" in an ISO Image in order to install it on my desktop. How is this done? and why is it necessary? I have downloaded ubuntu to cd & my documents, both cases, I cannot get it to complete.     Help!:(

---

### Post by pqwoerituytrueiwoq on 2011-03-24
download the iso 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
(10.04.x will recieve security updates longer than 10.10)
form windows use a app like [infrarecorder]("http://infrarecorder.org/") to burn the cd (or use a flash drive with [unetbootin]("http://unetbootin.sourceforge.net/"))

---

### Post by nesdunk on 2011-03-24
I already have this download on cd & my documrnts. using wubi to install ubuntu it gets partway then an error mesage: cannot locate file.

---

### Post by pqwoerituytrueiwoq on 2011-03-24
you do not need to use wubi
one you burn the cd reboot the computer
attempt to get to the boot menu (probably F10 or something) (some sometimes they are annoying with a 0 seconds delay to read the keys)
and select CD/DVD (or something to that nature)
or change the boot order in the BIOS so cd is 1st

---

### Post by jerome1232 on 2011-03-24
Okay first you do understand Ubuntu is an entire OS. Not just a program you run under Windows correct?

Wubi is a great way to try out Ubuntu but isn't meant as a permanent installation method. Since I don't have much experience with wubi specific issues I am going to refer you to the Wubi wiki, it has alot of great info for troubleshooting wubi.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


If you burn the image you downloaded to a cd you can try Ubuntu running from the cd without commiting to installing, just select "Try Ubuntu" from the boot list.  It will be slow since you are running from a cd.

If you wish to try a dual boot you can run the installer, be warned that you do have to resize partitions and as with all partitioning work there is a small risk (usually through user error) of losing your data, I always suggest you backup your personal files before attempting to repartition a drive, especially if you are inexperienced at it. That being said the automatic resize option will setup everything for you rather painlessly.


I hope my long winded post helped.

---

