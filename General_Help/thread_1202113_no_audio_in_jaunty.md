---
title: "no audio in jaunty"
date: 2009-07-01
forum: General Help
---

### Post by Hybrid86 on 2009-07-01
Just as the title says, I do not have any audio in my ubuntu installation. It is a fresh install on my brand new HP pavillion dv5. The headphone jacks work, but that's it.

Here is the output of lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```

Output of Alsa script site:
[http://www.alsa-project.org/db/?f=bb5de8bae17f537bd56165a8bd3974083f7f0e40](http://www.alsa-project.org/db/?f=bb5de8bae17f537bd56165a8bd3974083f7f0e40)

Output of "aplay -l":

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Audio device listed in the output of "lspci -v | less":

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3621
        Flags: bus master, fast devsel, latency 0, IRQ 2293
        Memory at df300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
```

---

### Post by colau on 2009-07-01
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Hybrid86 on 2009-07-02
Unfortunately, that guide is immensely outdated. Most of its links are dead, and the terminal commands it suggests are not recognized. :/

EDIT: It should also be mentioned that I followed the guide step by step, and nothing really worked.
This was my output for aplay -l however:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

It should also be noted, headphones work for whatever reason.

---

### Post by Hybrid86 on 2009-07-05
Bump

---

### Post by ivanvajar on 2009-07-05
Open Terminal and> gksu gedit /etc/modprobe.d/alsa-base.conf

Add
> options snd-hda-intel model=hp-dv5to the at the end of file and restart comp.

---

### Post by Hybrid86 on 2009-07-05
> **ivanvajar said:**
> Open Terminal and

Add
to the at the end of file and restart comp.

Just tried it. No dice :(

---

### Post by Hybrid86 on 2009-07-07
**Bump.**

I've still been looking activly for a solution with no luck. Here is a link to the bug report I've filed. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395318)

If anyone has a sugestion, I'd love to hear your advice. Not having sound really sucks.

---

### Post by joebeasley on 2009-07-09
I have the same chip and it seems I get no sound while the "external" option is selected.  Open alsamixer and mute "external".  It's all the way to the right.

---

### Post by turbuntu on 2009-07-09
had same problem installing pulse half solved the issue now can get sound with rythymbox/mplayer but can't get from web(firefox)

---

### Post by Hybrid86 on 2009-07-09
> **joebeasley said:**
> I have the same chip and it seems I get no sound while the "external" option is selected.  Open alsamixer and mute "external".  It's all the way to the right.

The "external" option doesn't seem to be there for me.

*I've already tried intalling pulse. Lost sound altogether.

---

### Post by Hybrid86 on 2009-07-10
I have also discovered that, while the headphones work, only VLC can play sound through them. I'm am going nuts here...

---

### Post by Hybrid86 on 2009-07-14
bump :(

---

### Post by 0re0 on 2009-07-14
bump

---

### Post by Hybrid86 on 2009-07-21
Sorry for the bump, but this is still a major issue for me. I have still not found a solution, though I have found many similar issues through google :(

---

### Post by vnrbhargav on 2009-07-22
BOSS  after trying the above said ove i got the startup sound...
but afterwards sound not working..


plz help dude..

---

### Post by AdAeternum on 2009-07-22
> I have also discovered that, while the headphones work, only VLC can play sound through them. I'm am going nuts here...This reminds me of a problem I had when I first installed Kubuntu Jaunty - I had no sound in certain circumstances but VLC was working fine - I went nuts installing drivers and messing around with Pulse Audio.

The problem at the end of the day, much to my embarrassment was that one of the volume sliders had its position set all the way to the bottom (not muted). I never checked it as I assumed all volume settings would be at their maximum on a fresh install. You may want to double check that.

Sorry if thats a bit obvious!

---

### Post by vishalag on 2009-07-22
I had the same problem when I installed ubuntu.
For me, reinstalling Alsa and selecting ALSA options under preference->sound worked.

---

### Post by 0re0 on 2009-07-22
i had this problemt for about two weeks trying different fixes on my hp till i came across the script and instructions from this link and has worked flawlessly since
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=hda+intel](http://ubuntuforums.org/showthread.php?t=1046137&highlight=hda+intel)

---

### Post by Hybrid86 on 2009-08-04
Just tried the script; script ran, but didn't sove the issue. Thank you though.

Any other ideas?

---

