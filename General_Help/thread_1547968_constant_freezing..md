---
title: "constant freezing."
date: 2010-08-07
forum: General Help
---

### Post by MXIIA on 2010-08-07
I am running Ubuntu 10.04 on an AMD64 computer with an ATI Raedon x1250 graphics card.

Everything runs fine for about 3 hours, then it will randomly stop working.
Symptoms:
   Mouse stops moving for 10 seconds
   Screen goes white
   Speakers start repeating last 10 seconds of whatever was playing
   Screen goes orange or purple with lines across it and random symbols...
at that point I hardware restart my computer and all is fine again

dmesg yields the following after every crash
> [ 5334.171171] [drm:edid_is_valid] *ERROR* Raw EDID:
[ 5334.171174] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171176] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171179] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171181] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171183] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171186] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171188] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171190] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 5334.171192] 
[ 5334.171196] radeon 0000:01:05.0: HDMI Type A-1: EDID invalid.
[ 5334.171203] [drm:radeon_dvi_detect] *ERROR* HDMI Type A-1: probed a monitor but no|invalid EDID
 

and my computer info is as follows
> 
mxiia@homebox:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:05.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
03:06.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)


---

### Post by Jcink on 2010-08-07
I'm also having the same issues with the same card, anyone have any ideas?

---

### Post by falstart on 2010-08-07
I have nearly the exact same problem. The only difference with mine is that my computer resets. I believe my graphics card (nVidia) is overheating and sending the processor a NMI.

---

### Post by MXIIA on 2010-08-07
This seems to be a pretty common problem, not only in this topic, but a quick google search for "ubuntu 10.04 freezes" yields MUCH more than "fedora f13 freezes"

---

### Post by MXIIA on 2010-08-10
I would like an answer/response

---

### Post by MatthewAdams on 2010-08-10
It looks to be a graphics card issue where it tries to probe a monitor that isn't there. Hard to say if it's an overheating issue....have you run any sensor programs, like KSensors, or does ATI have a utility which monitors the temp of the card? 

If you're using a proprietary ATI driver, have you tried downgrading the version? 

I'm a noob, just tossing around some ideas.

---

### Post by MXIIA on 2010-08-12
> **MatthewAdams said:**
> It looks to be a graphics card issue where it tries to probe a monitor that isn't there. Hard to say if it's an overheating issue....have you run any sensor programs, like KSensors, or does ATI have a utility which monitors the temp of the card? 

If you're using a proprietary ATI driver, have you tried downgrading the version? 

I'm a noob, just tossing around some ideas.

Thank you for your response.

It obviously is a graphic card issue :P

Mine isn't over heating, as far as I know

And, ATI discontinued it's proprietary driver forcing me to use the (obviously) unstable open sourced one, this is the source of my problems I believe. I cannot find the old version of the ATI driver and if I could I'm not sure it it'd work with 10.04, it worked with 9.04 and 9.10 is when it was discontinued.

---

### Post by dino99 on 2010-08-12
old xorg.conf can be blamed most of the time, so rename or remove it:

sudo rm -f /etc/X11/xorg.conf

you can add this ppa to synaptic repo tab:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

( if you have previously installed a driver from ati source, remove it)

---

### Post by MXIIA on 2010-08-12
> **dino99 said:**
> old xorg.conf can be blamed most of the time, so rename or remove it:

sudo rm -f /etc/X11/xorg.conf

you can add this ppa to synaptic repo tab:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

( if you have previously installed a driver from ati source, remove it)
So you merely want me to rename/remove my xorg and add that ppa? is there anything else I should do besides adding that ppa?

edit: apparently I have no xorg.conf...

I attempted to install fglrx, xserver-xorg-video-ati and xserver-xorg-video-raedon and I do not know if it did anything.

---

### Post by rdratlos on 2011-07-06
> **MXIIA said:**
> I am running Ubuntu 10.04 on an AMD64 computer with an ATI Raedon x1250 graphics card.

Everything runs fine for about 3 hours, then it will randomly stop working.
Symptoms:
   Mouse stops moving for 10 seconds
   Screen goes white
   Speakers start repeating last 10 seconds of whatever was playing
   Screen goes orange or purple with lines across it and random symbols...
at that point I hardware restart my computer and all is fine again

dmesg yields the following after every crash
 

and my computer info is as follows

Could you please post the complete dmesg log? There might be a fix for this problem. See [https://lkml.org/lkml/2011/6/21/244](https://lkml.org/lkml/2011/6/21/244). What's the name and vendor of your board?

---

