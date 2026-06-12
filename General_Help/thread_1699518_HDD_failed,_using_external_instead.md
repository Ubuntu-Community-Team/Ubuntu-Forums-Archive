---
title: "HDD failed, using external instead?"
date: 2011-03-03
forum: General Help
---

### Post by chunkylover on 2011-03-03
Hi, I've been really struggling to find anything online pertaining to my dilemma:

I have a Sony Vaio VGN-N31S, it is old and the degraded hard drive has recently failed. I can run "try ubuntu" from a live CD, but this is hardly a long-term solution.

I have a Phillips 180GB External USB Hard Drive, which I would like to install Ubuntu on, allowing me to download programmes as well as save settings within Ubuntu.

Is there any way in which I can easily install Ubuntu 10.10 on to a USB hard drive, and then proceed to use the USB drive as my main hard drive (I have an inkling this is possible, as my BIOS does allow me to boot from a USB drive.)

Thus far, any attempts to install have failed. The installation is very slow at the "Preparing to install Ubuntu" screen where it advises you to connect to a power source, connect to the internet, etc. 

Could anybody shed any light on this issue, or will I have to simply buy and fit a new internal hard disk?

---

### Post by Austin25 on 2011-03-03
First, if your CD drive is too slow, you can use unetbootin with a flashdrive. Second, the installer should be able to detect your drive, but at Step 4 you need to change to your drive, and at Step 7 you will need to click advanced and set it to install the boot loader on your external drive.

[Source.]("http://scottlinux.com/?p=242")

---

