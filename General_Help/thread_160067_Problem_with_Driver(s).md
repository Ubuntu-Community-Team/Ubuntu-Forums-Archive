---
title: "Problem with Driver(s)"
date: 2006-04-14
forum: General Help
---

### Post by invalid06 on 2006-04-14
Hi, I'm a bit new to Linux. I ordered my Ubuntu disks back when 5.04 was out, and after about 10 Windows screw-ups i finally decided to jump over to Linux, and I've run into a bit of a problem. I have a Dell Dimension 2400 Series Desktop computer with nearly EVERYTHING it has built into the mobo. My Vid card is an Integrated Intel Extreme Graphics 82845G/GL/GLE, and I can't seem to find a driver for it ANYWHERE would anyone know where i could find one? 640x860 is REALLY annoying. And also, I can't get hardly anything to install right (LimeWire mainly) anyone care to help me out with that? Also, I'm having a bit of a problem finding the Plugin for RythemBox that allows the playing of .mp3 files. Converting .mp3's to .ogg gets annoying after a while.

Thanks in advance,
invalid06

---

### Post by dermotti on 2006-04-14
run **sudo dpkg-reconfigure xserver-xorg**

Select vesa as your driver

Near the end of the setup it should give you options for resolutions, just check the resolution you want, and uncheck all the ones you dont want.

Once yer done reboot or restart X.

---

