---
title: "can't open flash drive"
date: 2010-07-18
forum: General Help
---

### Post by imparja on 2010-07-18
I've had this problem for years but never had the time or the know how to fix it. I still use hardy heron.

I insert the flash drive into the usb terminal and it registers that I've inserted it. However when I go to open it or when I drag files to the flash drive icon nothing happens.

I want to transfer some files from my old computer (hardy) to my new one. Btw I tried formatting the flash drive and that didn't work. Please someone help.

---

### Post by balta on 2010-07-18
Hi there,
well, that's strange ... 
... I've never had (or heard of) this type of issue nor I have never used hardy, so I'll just tell you my common-sense-driven ideas.
Have you tried other USB devices, or, have you tried the same USB device under other OS (better would be under another Hardy)?
Can you use the terminal to navigate to your drive?
And I don't want to sound mean whit this but, why don't you try an upgrade?
Sorry for my poor help :( (if you can actually call *that* an help :P)

---

### Post by imparja on 2010-07-18
yeah i tried the mouse and keyboard they work. but my ipod and flash drive can't be mounted. It seems the problem is only storage devices.

---

### Post by balta on 2010-07-19
If you try
```
sudo fdisk -l
```
or
```
sudo lsusb
```
(actually I'm not sure if "sudo" is necessary ... oh well)
In a terminal can you see the USB drive listed?
If yes, can you navigate to it using the "cd" command?

In case they are not listed, you may want to try to mount them using a guide like [this]("http://www.novell.com/coolsolutions/feature/11637.html").
(found it in another ubuntuforums post and said to be working)

Hope it can give a little help, until someone more expert comes down here ;)

---

### Post by imparja on 2010-07-20
yes thanks I can see it listed but I don't know what you mean by navigate the "cd command". Can you please explain. thanx so much no one else wants to help me.:(

---

### Post by vikas.sood on 2010-07-20
You can manually mount the usb drive.
open a terminal..
cd /mnt
sudo mkdir usbdrive
mount -t <file-system> /dev/sdXY /mnt/usbdrive

<file-system> is the file system of your usb
XY would be the /dev identifier of your usb..you are able to see the usb drive using sudo fdisk -l.

after mounting cd /mnt/usbdrive

Enjoy!!

---

