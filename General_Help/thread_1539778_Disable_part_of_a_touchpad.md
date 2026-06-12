---
title: "Disable part of a touchpad"
date: 2010-07-27
forum: General Help
---

### Post by Snowboardr on 2010-07-27
I'm relatively new to linux. I've played with it occasionally over the years so I know a bit, but not much. What I'd like to know is if it's possible to disable part of a touchpad rather than the whole thing. 

I have an HP Mini 210 running 10.04 and the touchpad blends the buttons into the surface, so the buttons also count as the touchpad. I'd like to be able to disable the bottom half inch of so to make click and drag a bit easier.

---

### Post by P4man on 2010-07-27
I think its possible. In xorg.conf you can define a whole range of options for the touchpad. Assuming it uses a synaptics driver; have a look here:
[http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics)

Note the leftedge, rightedge, topedge etc lines. To have an idea of the values to put there use synclient (see that same page further down).

---

### Post by Snowboardr on 2010-07-27
Thanks, that seems simple enough. The only problem though is that for some reason my touchpad isn't showing as a synapic even though it is.

---

### Post by P4man on 2010-07-27
What makes you say it is; and why do you say its not showing up as one?

---

### Post by Snowboardr on 2010-07-27
I've spent that last few days trying to get two finger scrolling enabled.

```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
```

That returns "unable to find device SynPS/2 Synaptics Touchpad"

---

### Post by P4man on 2010-07-27
can you post the output of lspci and lsusb?

---

### Post by Snowboardr on 2010-07-27
lspci
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Multimedia controller: Broadcom Corporation Device 1615

```

lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0408:0ff1 Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by P4man on 2010-07-27
Googling that Quanta device reveals its indeed not a synaptics touchpad but an Alps one. And what i found were mostly bug reports; like this one:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/527890](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/527890)

and this long thread:
[http://ubuntuforums.org/showthread.php?t=1316361](http://ubuntuforums.org/showthread.php?t=1316361)

The short version of it seems to be that you are lucky its working as a touchpad; but I wouldnt have much hope to configure it much beyond that. Wont stop you from trying the instructions I linked earlier though; just for the Alps touchpad

[http://wiki.archlinux.org/index.php/Touchpad_Synaptics#ALPS_Touchpads](http://wiki.archlinux.org/index.php/Touchpad_Synaptics#ALPS_Touchpads)

---

### Post by Snowboardr on 2010-07-27
I better get to work than. Haha.
Thanks for the help.

---

