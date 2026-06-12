---
title: "LG Versa; BitPim; HELP"
date: 2010-01-10
forum: General Help
---

### Post by Pgod on 2010-01-10
I've been trying to solve this problem for DAYS now, without any progress. I've searched the forums for a long time before even starting this thread. So now I need help, PLEASE. I don't want to have to use WINDOWS in order to sync my phone with my computer, that's crap and there has to be a way. 

I have Ubuntu 9.10 and I'm trying to sync my LG Versa VX960V07. When I plugged it in to begin with, it was set on Auto-Sync Music, and the phone showed that it was connecting to the computer. I set it on Data-Sync and nothing happened when I plugged it in. I set it to Ask on Plug-in, and again nothing happens, and the box on my phone that says "Sync Data; Sync Music" does not pop up like it does when using windows. 

First I tried installing a bunch of different music programs, Songbird, Amarok, K3B, etc and none of them work with my phone. I can't even install the MTP add-on for songbird, it's not supported under linux. 

Then I tried sudo apt-get install mtp-tools, which worked. Then MTP-detect, which showed no device. 

I also tried the command for searching for drives attached. And it did not show a USB drive attached. My computer simply does not detect my phone.

Then I tried this:

[http://www.ntwrkguru.com/?p=11](http://www.ntwrkguru.com/?p=11)

Installing BitPim, which does not support the LG Versa, but the new 1.0.7 testing branch does. So I followed the tutorial on that page, installing Alien and trying to convert the RPM to DEB. I don't even know what these commands mean, I'm not a linux Guru, but I'm learning. I tried everything and spent like 3 hours going through this tutorial to no avail. Is it suppose to create a .deb file where the RPM is? If so it doesn't work, and it won't launch BitPim for me. I have no idea what's going on. When I try: 

sudo alien -ic ~/Downloads/bitpim-1.0.7.20090805-0.i386.rpm

I get:

error: incorrect format: unknown tag
    dpkg --no-force-overwrite -i bitpim_1.0.7.20090805-1_i386.deb
(Reading database ... 175361 files and directories currently installed.)
Preparing to replace bitpim 1.0.7.20090805-1 (using bitpim_1.0.7.20090805-1_i386.deb) ...
Unpacking replacement bitpim ...
Setting up bitpim (1.0.7.20090805-1) ...


The "error" I get, I don't know what it means, but either way, this isn't working.

I'm getting so frustrated with this and the forums are my last hope before I install Windows again. I really don't want to admit defeat and use windblows. PLEASE HELP ME!!

 - Phil.

---

### Post by Pgod on 2010-01-11
Bump cuz I'm amazed at how many new posts are on this forum everyday. Feel like posts get easily buried and I'm up agaisnt a wall with this problem

thanks again and in advance!

---

### Post by Pgod on 2010-01-13
Another bump. I'm in tears here!!

---

### Post by haemphyst on 2010-01-29
Another bump, from another user...  Same phone, same OS.  I'm actually even further behind than the OP, I can't even get bitpim to launch, so I need a little bit of help there...

When I run lsusb, here's my output:
haemphyst@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
haemphyst@ubuntu:~$ 

The Verizon network connects, and I can access the internet via the tethering, so I know that the device is recognized as "correct", and I believe that I have adequate "rights" to the USB device.

Any suggestions?  Please?  Help a couple of relative noobs out...

---

