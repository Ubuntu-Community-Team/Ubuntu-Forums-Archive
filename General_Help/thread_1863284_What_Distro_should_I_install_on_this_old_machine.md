---
title: "What Distro should I install on this old machine?"
date: 2011-10-17
forum: General Help
---

### Post by Thetri on 2011-10-17
Currently installing a Windows XP 32 bit professional edition, got the hdd split into two partitions, going to install a linux distro on the other partition. I'm wondering which one I should try. I know your going to say install your favorite. I tried that and it didn't pick up my wireless card, i've other distros as well and i run into the same issue. I finally got one working, which is Pardus 2011. I'm not a fan of it, I would like to get something like mint/ubuntu but the wireless wont work and I cannot possibly connect with ethernet because I would have to unplug everything and carry it up flights of stairs. Any here is my specs ```
My Specs: Operating System
Win Xp Professional 32 bit
CPU
AMD Athlon 64 X2 4400+ 37 °C
Brisbane 65nm Technology
RAM
2.0GB Dual-Channel DDR2 @ 330MHz (5-5-5-15)
Motherboard
Dell Inc. 0RY206 (Socket AM2 )
Graphics
DELL SE198WFP @ 1440x900
ATI Radeon HD 2400 PRO (Dell) 48 °C
Hard Drives
244GB Seagate ST325082 0AS SCSI Disk Device (SCSI)
Optical Drives
HL-DT-ST DVD+-RW GSA-H73N SCSI CdRom Device
```

I believe my wireless is a broadcom if that helps. Thanx

---

### Post by rene8 on 2011-10-17
Try the last LTS Ubuntu realease (10.04) rather than the newest one.

---

### Post by Thetri on 2011-10-17
thanks for the reply, would mint 10.04 be the same? i prefer mint over ubuntu.

---

### Post by zhogan85 on 2011-10-17
> **Thetri said:**
> thanks for the reply, would mint 10.04 be the same? i prefer mint over ubuntu.

Linux Mint 9-Isadora, is based on Ubuntu 10.04. 

You might also, try Lubuntu, as a lighter version of Ubuntu.

Although, looking at your specs, they are higher than mine, and Ubuntu 11.10 works great for me. But if you prefer Mint, try the most recent version.

---

### Post by cbowman57 on 2011-10-17
You may have to temporarily connect via LAN cable to instll b43-cutter, which should support your Broadcom wifi.

---

### Post by Thetri on 2011-10-17
> **zhogan85 said:**
> Linux Mint 9-Isadora, is based on Ubuntu 10.04. 

You might also, try Lubuntu, as a lighter version of Ubuntu.

Although, looking at your specs, they are higher than mine, and Ubuntu 11.10 works great for me. But if you prefer Mint, try the most recent version.

Not a fan of the new Ubuntu interface. I already tried the latest version of mint and my wireless does not show up.

---

### Post by drawkcab on 2011-10-17
With broadcom, it helps a bunch if you install while your wifi card is enabled.  For example, make sure it is turned on and enabled in windows before you go to install so that it will be recognized during installation.

Second, the firmware cannot be installed on the cd so you have to jack into your ethernet port and use the restricted drivers app to download the firmware for your card.  Once it is installed you can unplug and then connect wirelessly.

There are some distros that include the firmware but I couldn't tell you which ones anymore.  But I wouldn't want to choose a distro based soley on that requirement as it is so easy to get it working in ubuntu or mint by plugging it in for a second.

---

### Post by Thetri on 2011-10-18
> **drawkcab said:**
> With broadcom, it helps a bunch if you install while your wifi card is enabled.  For example, make sure it is turned on and enabled in windows before you go to install so that it will be recognized during installation.

Second, the firmware cannot be installed on the cd so you have to jack into your ethernet port and use the restricted drivers app to download the firmware for your card.  Once it is installed you can unplug and then connect wirelessly.

There are some distros that include the firmware but I couldn't tell you which ones anymore.  But I wouldn't want to choose a distro based soley on that requirement as it is so easy to get it working in ubuntu or mint by plugging it in for a second.

Its not worth the time and effort that is required to plug in the cable. I would have to unplug the tower and bring it up 2 flights of stairs. Then i will have to unplug my other tower. plug in the old machine find a working ethernet cable, attach it, download drivers, unplug everything. Carry it back downstairs, plug it in. I think i would rather install pardus 2011, much easier.

---

### Post by kurt18947 on 2011-10-18
> **Thetri said:**
> Its not worth the time and effort that is required to plug in the cable. I would have to unplug the tower and bring it up 2 flights of stairs. Then i will have to unplug my other tower. plug in the old machine find a working ethernet cable, attach it, download drivers, unplug everything. Carry it back downstairs, plug it in. I think i would rather install pardus 2011, much easier.

 I understand that, I have something similar though not as extreme. I have an old TrendNet TEW-424UB (RealTek 8187B I think) that I keep just for that purpose. It's been plug & play on every Ubuntu distro I've tried since 8.10 or 9.04. It's pretty slow but I use it to install restricted drivers etc. then remove it and put it in the drawer until I need it again.

---

### Post by Thetri on 2011-10-18
> **kurt18947 said:**
> I understand that, I have something similar though not as extreme. I have an old TrendNet TEW-424UB (RealTek 8187B I think) that I keep just for that purpose. It's been plug & play on every Ubuntu distro I've tried since 8.10 or 9.04. It's pretty slow but I use it to install restricted drivers etc. then remove it and put it in the drawer until I need it again.

thats still a lot of work just to get wireless to work. i have to go to stores a shop around for usb wifi adapters that are rare in these parts of canada. Maybe i'll use a older version for now and upgrade later.

---

### Post by kurt18947 on 2011-10-18
> **Thetri said:**
> thats still a lot of work just to get wireless to work. i have to go to stores a shop around for usb wifi adapters that are rare in these parts of canada. Maybe i'll use a older version for now and upgrade later.

 That would complicate things. There aren't all that many adapters that are no-fuss installs and it sounds like your choices are not limitless. If you're dealing with many models from Broadcom or Ralink things can get a little ..... complex. ;)

---

### Post by Thetri on 2011-10-18
Just tried mint 9 and ubuntu 10.04. They dont work, going to try ubuntu 11.10. Cant seem to get wireless drivers on the xp boot either, looks like im going to scrap that idea and return to full linux box. If 11.10 fails to pick up my wireless im going to go back to pardus 2011, anyone else have any suggestions?

---

### Post by claracc on 2011-10-19
You can try lubuntu 11.04 from live CD in order to see if your wireless works.

Lubuntu 11.04 is very quick, light  and stable

---

