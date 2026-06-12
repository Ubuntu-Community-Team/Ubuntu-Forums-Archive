---
title: "[COMPLETELY new to ubuntu] No sound! plz help"
date: 2009-09-15
forum: General Help
---

### Post by gka88 on 2009-09-15
Hi guys im sure this has been discussed in several different threads, and I have searched all over and found a bunch of topics regarding this.
 
the problem is, I just installed ubuntu and how no experience with that or with linux etc. what so ever. i just cannot seem to find a single forum online that explains the sound issue in a understandable way.

so yeah i have no sound what so ever in ubuntu 9.04 that i installed the other day. i like ubuntu so far but obvi this kinda sucks.

yes i have checked that the volum is not muted
yes i have tried the different settings
yes i have tried headphones
yes i have searched all over

can someone PLEASE help me fix this, and explain in detail how to do it?
thanks guys

---

### Post by Lord foff on 2009-09-15
I had this problem when i first installed ubuntu.
It may be that your using an uninstalled sound card.

---

### Post by P4man on 2009-09-15
perhaps start with providing us some info: which version ubuntu, which soundcard or system?

Open a terminal and type

```
aplay -l
```
and```
 lspci
```

And copy paste the results here. That way we can perhaps know in which direction to search.

---

### Post by gka88 on 2009-09-15
all right heres what i got:
                          
[SIZE=3][SIZE=1]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/SIZE][/SIZE]
[SIZE=3][SIZE=1]
[/SIZE][/SIZE]
[SIZE=3][SIZE=1] lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller[/SIZE][/SIZE]


[SIZE=3][SIZE=1]this could literally be written in the language of the wahuhahu tribe on the vanuatu islands and id still understand nothing :p[/SIZE]
 [/SIZE]

---

### Post by P4man on 2009-09-15
the first command lists all available sound devices, the second command lists all devices on your motherboard.

You got 2 "soundcards" in that machine, one in your videocard for HDMI audio (like when connecting to a tv with hdmi cable), and one regular onboard sound, to which I assume you connected your speakers?

Im guessing you got the wrong soundcard as default. You want to have the "STAC92xx Analog". Have a look in system > prefences > sound make sure you got the right default mixer.

---

### Post by gka88 on 2009-09-15
Still not working :(
when i try testing HDA ATI SB STAC92xx Analog ALSA in "sound events" i get the error:

audiotestsrc wave=sine freq=512!
audioconvert! audioresample! gconfaudiosink:
could not open audio device for playback

---

### Post by gka88 on 2009-09-15
anyone? dont wanna have to go back to vista...

---

### Post by P4man on 2009-09-15
googling I do see a few bug reports relating to that soundcard, and some solutions upgrading and/or compiling alsa.

So first question: did you install all updates?
If you did, perhaps you can try enabling backports to pull in upstream drivers:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Im not sure that will upgrade your alsa though.

Last thought: download and compile a more recent version of alsa. if you don't know how, then perhaps this can help:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

afterthought: see if it works with Karmic?

---

### Post by Hamadp on 2009-09-15
[LEFT]dude i have the exacpt same problem, ill tell you if i find anything works for me 
[/LEFT]

---

### Post by gka88 on 2009-09-15
please do man!

---

