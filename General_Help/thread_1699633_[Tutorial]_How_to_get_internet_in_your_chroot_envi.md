---
title: "[Tutorial] How to get internet in your chroot environment"
date: 2011-03-03
forum: General Help
---

### Post by James78 on 2011-03-03
This is a simple tutorial on how to get internet access in a chroot environment.

This can be very useful in many situations. What I primarily use it for is Reconstructor. I use Reconstructor to deconstruct the Ubuntu image into a working directory, run this script to enable internet and chroot into the working directory. Then I make all my modifications to the Ubuntu image (updating all the packages to the latest versions), then rebuild it back into a LiveCD with Reconstructor.

The requirements are:
Your chroot will be running under a main OS, which is already connected to the internet.

Now for the good parts. My program is fairly simple.
```
icearmy@opti-hacker:~$ ./chroot-internet.sh -h
Usage: ./chroot-internet.sh [options]
    -h      : Display help message
    -w      : Path to working directory
icearmy@opti-hacker:~$ sudo ./chroot-internet.sh -w /path/to/chrootdir/
Mounting system directories...
Enabling internet...
Starting chroot...
root@opti-hacker:/# apt-get update
...
Get:15 http://archive.ubuntu.com maverick-updates/main Sources [89.3kB]
Get:16 http://archive.ubuntu.com maverick-updates/restricted Sources [778B]
Get:17 http://archive.ubuntu.com maverick-updates/main i386 Packages [242kB]
...
```It's as simple as that! Enjoy!

---

