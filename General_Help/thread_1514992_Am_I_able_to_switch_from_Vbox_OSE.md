---
title: "Am I able to switch from Vbox OSE"
date: 2010-06-21
forum: General Help
---

### Post by OxentroT on 2010-06-21
Hello, I was wondering if it was possible to switch from Vbox OSE to the full version provided by sun without having to have to back-up and re install my OS on it again. Im not sure how I installed this version, must not have been paying attention. :mad: I just need USB support.

Thankyou

---

### Post by C.S.Cameron on 2010-06-21
After upgrading you may have to create new virtual machines but you can "Use existing hard disk" and point Virtual Media Manager to your existing .vdi files.
Nothing will be lost.

Edit:
I carry an XP.vdi around on a pendrive for use on different Ubuntu machines in case I should ever need AutoCAD away from my office computer.

---

### Post by Leppie on 2010-06-21
i've switched from the ose version to the puel version without a glitch.
just install the puel version, and most probably the vm will already be there when you launch it ;)

---

### Post by OxentroT on 2010-06-22
Thank You for the replies):P

Okay. I did a 

```
 sudo apt-get remove --purge virtualboxOSE
```

and then a

```
sudo apt-get remove virtualboxOSE
```

Afterwards I installed the complete version from Oracle. To my surprise my WinXP vm was still there, unscaved and now it has support for USB devices!

But I am still having some problem in being able to access my thumb drive. It recognizes that it is in fact hooked up, however, there is nowhere to access it. 

Thankyou.

---

### Post by Leppie on 2010-06-22
did you put yourself in the virtualbox group?
once you are a member of that group, at the bottom right corner there's a couple of tiny icons. one of them is a usb plug, if you right click on that icon the usb devices connected to your system should appear. click the one you want to enable/disalbe. if a check sign appears to the left of the device, it's enabled in the host machine.

---

### Post by C.S.Cameron on 2010-06-22
I found a big improvement with the latest version. A lot of stuff seems to work without installing guest additions in 3.2, probably still  good idea to install it though.
You should also be able to find your USB up at the top under Devices/USB Devices.

---

### Post by 3Miro on 2010-06-22
If you detect the device but cannot access it:

As pointed out, you have to be member of virtualbox usergroup, however, that is not always enough. Once I had to make myself member of usergroup ls to get my printer to work.

You can try to run virtualbox with:
```
gksudo VirtualBox
```
WARNING: this is a hazardous operation and can damage your OS. It worked for me in the past, but there is no guarantee.

---

### Post by macstar on 2010-06-22
you can switch from ose to the oracle version without any problem. actually, i did the same today and it kept my installed win7 in virtual environment. :)

---

### Post by OxentroT on 2010-06-24
Thank you for the great advices every one! Much appreciation 

sudo Rock-On :guitar:

---

### Post by Leppie on 2010-06-25
you're welcome :)

so everything is working fine now?

---

