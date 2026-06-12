---
title: "green screen of death?"
date: 2010-08-11
forum: General Help
---

### Post by goltoof on 2010-08-11
Anyone else ever get a speckled green screen that freezes everything?  It comes out of nowhere, not program specific.  The screen just gets covered in green dots and I have to reboot.

I get this at least every other day.  I'm using ATI Radeon HD 5500 card, which I think may be suspect but I'm not sure.

I'm not savvy on error logs. Are there any log files I can check to see what's causing my system to freeze?

---

### Post by AlphaLexman on 2010-08-11
You should have taken the **blue** pill...

---

### Post by goltoof on 2010-08-11
> **AlphaLexman said:**
> You should have taken the **blue** pill...

lol

---

### Post by goltoof on 2010-08-12
All Matrix banter aside though.. anyone here to actually help?

I'm getting sick of these freezes. I know Ubuntu is better than this.  I've spent too much time screwing around with graphics drivers just to get my monitor working, now this.  Can someone at least give a hint as to what error logs I should be checking?

What I'd really like is to setup some escape sequence to get out of /restart gnome when it freezes like this without having to hard reboot, if possible.

Anything, please.

---

### Post by Unknown-Demon on 2010-08-12
What version of ubuntu are you using?

---

### Post by AlphaLexman on 2010-08-12
Post your xorg.conf file:
```
cat /etc/X11/xorg.conf
```

---

### Post by goltoof on 2010-09-10
only happened a few times this month, now it's 4 times today


```


Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual	3648 1230
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3648 1230
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection



```

---

### Post by WorMzy on 2010-09-10
Is it actually crashing the PC, or is it just the display locking up?

i.e. can you perform the [Magic REISUB]("http://en.wikipedia.org/wiki/Reisub") key combination to safely restart?

---

### Post by hakermania on 2010-09-10
Green is better than blue :P

---

### Post by goltoof on 2010-09-10
> **WorMzy said:**
> Is it actually crashing the PC, or is it just the display locking up?

i.e. can you perform the [Magic REISUB]("http://en.wikipedia.org/wiki/Reisub") key combination to safely restart?

The display locks up, can't do anything and need to reboot.

I'll try that Magic thing next time it happens though.

---

### Post by goltoof on 2010-09-10
> **hakermania said:**
> Green is better than blue :P

Word, but I'd rather have neither.

---

### Post by QIII on 2010-09-10
Things that start out happening once in a while and progressively get  worse until they happen frequently generally put me in a mind to examine  hardware faults.

The green color makes me think it is the card or the driver rather than the OS.

I'm assuming your card is fairly new (but "new" does not mean "perfect".  I've had new cars back into the shop at the dealer several times in the first few weeks).

It may be something as simple as rampantly multiplying dust bunnies or a loosening card.

Before going to extreme measures, check the simple things first to  eliminate them.  Open the case, blow out the dust bunnies and ensure the  card is snuggly seated.  Even though your card is secured by a screw,  it can still partially dislodge because of the slight vibrations of the  fan or because you accidentally bumped your machine somewhere along the  line.

If you want to pull the card out entirely for a moment, you can look for blistered capacitors and scratches on the traces.

I would say that 90% of the time someone calls me with their hair on fire thinking something is wrong with their machine, it's the really simple things.  Recently, one of our foster kids' moms called me frantic.  Her monitor wasn't working.  Turns out the card wasn't secured by a screw and she had set the machine down too hard when moving it.  The card was completely unplugged.  Should have charged her for the service call.  ;)

---

### Post by goltoof on 2010-09-13
> **QIII said:**
> 
The green color makes me think it is the card or the driver rather than the OS.



Happened again today.

I pulled out the card and it all looks fine, not loose or damaged. I'll try another card soon enough.

No doubt it could still be the card, or maybe the drivers.  I spent so much time fumbling with the drivers just to get it to support two monitors.

---

### Post by tsvim on 2010-09-13
Not sure if related.
I get a grey screen of death with lines vertically on the screen, reason I think it might be related as I have ATI Radeon HD 4350.  I'm using FOSS drivers. For some reason though I can't even SSH into my machine. Everything freezes. Help.
More info:
running 10.04 Kubuntu (amd64) on custom built iCore5 with 4Gig of RAM, software RAID1 for /, RAID5 for /home
Freezes occur about once-twice a week.

---

### Post by goltoof on 2010-09-15
It's done it 3 times now in the last 15 MINUTES!!   Each time I come to post here because this keeps happening, then it freezes as I type! It doesn't matter what I'm doing, it's purely random.

Is there anything else I can check, besides reinstalling graphics drivers, or trying a different graphics card?

I still don't even have a clue if it's graphics related. This is a decent machine with tons of resources.  Someone throw me a bone, please.

Maybe this helps?
```

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configur
ation
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68d9
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
03:06.0 Ethernet controller: VIA Technologies, Inc. VT6105M [Rhine-III] (rev 96)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet co
ntroller (rev 03)



```

---

### Post by goltoof on 2010-09-21
this sucks...

---

### Post by goltoof on 2010-10-05
Switched to Nvidia (just had to wait for the bucks for this solution).  From the looks of it Nvidia support is way better than ati, as far as linux drivers go. Apparently so since setup was a breeze.

All is well now...

---

