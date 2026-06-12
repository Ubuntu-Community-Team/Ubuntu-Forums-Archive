---
title: "How to boot windows 7 partition"
date: 2012-03-28
forum: General Help
---

### Post by xkcd1253 on 2012-03-28
Hey, I'm using Ubuntu server 11.10 and I made it on a partition. The computers set so that it automatically boots from ubuntu server and I want to boot Windows. Whenever I try to hold down shift, GRUB doesn't load and I also tried to change the settings so that GRUB launches automatically, but it didn't work. How can I boot the Windows 7 partition?

---

### Post by oldfred on 2012-03-29
Welcome to the forums.

I do not believe the server install is a liveCD. To make repairs you will need a liveCD so download the desktop version of Ubuntu as a liveCD or USB.

We need you to run boot info script to see what is installed where.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Or in LiveCD you can directly download and run:
The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

---

