---
title: "How do I install ubuntu from a memory stick or sd card?"
date: 2010-03-22
forum: General Help
---

### Post by kokkus on 2010-03-22
Hey. My new pc doesn't have a cd rom so I have to use a memory stick, usb hard driver or a SD card.
So how do I install ubuntu?
For some sh'itty reason I got windows vista installed here which is more frustrating then everything else I have tried.
Please help me out here. Thanks

---

### Post by akakingess on 2010-03-22
Try this out and see if this helps, just googled your subject and got [this]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by kokkus on 2010-03-22
Thanks but that was for fedora. and I don't wanna install ubuntu under windows. I want to install it on its own partition.

---

### Post by Bradtek on 2010-03-22
```
sudo apt-get install usb-creator
```

(or if that doesn't work)
```

sudo apt-get install usb-creator-gtk
```

Then

System | Administration | USB Start up Disk Creator

BTW the other link is NOT just for fedora
it is for Windows and Linux, compile source for any linux distro

---

### Post by kokkus on 2010-03-22
> **Bradtek said:**
> ```
sudo apt-get install usb-creator
```

(or if that doesn't work)
```

sudo apt-get install usb-creator-gtk
```

Then

System | Administration | USB Start up Disk Creator

BTW the other link is NOT just for fedora
it is for Windows and Linux, compile source for any linux distro

I can't do sudo commands in windows. Or didn't you read my message? I am in Vista now and my pc doesnt have a cd rom so I have to use a usb mem stick or a SD card to install ubuntu. But I want to install it on its own partition and not under the windows OS..

---

### Post by kokkus on 2010-03-24
Bump!

I installed Wubi but how do I run it, and how do I fully install ubuntu under wubi?

---

### Post by -grubby on 2010-03-24
Download and install [unetbootin](http://unetbootin.sourceforge.net/). Then start it. Select "Ubuntu" as your distribution and it should be smooth sailing from there.

---

### Post by kokkus on 2010-03-24
Thanks alot.
Ok so now when I have ubuntu under windows (Wubi), how do I install it on its own partition so it doesnt have to be under windows?

---

### Post by Fenris_rising on 2010-03-24
If you have installed unetbootin, whether in windows or ubuntu under wubi, use this to create a bootable usb stick with the ubuntu of your choice. Once set up do the following -

Insert the stick, reboot, and hit the [esc] key a few times as the PC comes back up, this usually brings up the boot menu where you can select which device to boot from it may be a different key for you, select the usb stick when you get as far as the partitioner part of the install select the side by side option or to use the largest available empty space.

You will also find the search facility, top right, useful as well.

regards

Fenris

---

