---
title: "Speakers Work but not Headphones"
date: 2012-01-09
forum: General Help
---

### Post by Hipster Doofus on 2012-01-09
11.10.
No matter what I set in the Mixer I can't get sound through the headphones. I hope I'm in the right area to change the sound settings.

```
root@HipsterDoofus:/home/hipster# lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Cypress [Radeon HD 5800 Series]
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
09:00.0 IDE interface: Marvell Technology Group Ltd. Device 914d (rev 10)
0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
root@HipsterDoofus:/home/hipster# 
```Any clues?

---

### Post by carl4926 on 2012-01-09
It seems like you have 2 audio devices
Which are you using?

---

### Post by Hipster Doofus on 2012-01-09
Not really sure. Whatever one works. :D

I have onboard sound & I have connected the sound to.....after trying to remember I can't. Typical.

In the 'mixer' the only one that has the headphone option is HDA Intel (Alsa mixer) if that helps.

---

### Post by carl4926 on 2012-01-09
You have to assign the system to one or the other
You decide
Then make sure you toggle the mixer settings accordingly.

---

### Post by Hipster Doofus on 2012-01-09
Thought I better post back here before I trash something. I've figured out which sound I want but can't figure out how to set it in the system.

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
[B]card 0: Intel [HDA Intel], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1[/B]
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```The one I want is highlighted. Trying to set up a fresh install of 11.10. Actually anyone of the top two will do.

---

### Post by Z06Gal on 2012-01-09
I run Mint 12 and had the same issue until I saw a post on the Mint forums about this issue.  The fix is in updating the driver:

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Mint thread: [http://forums.linuxmint.com/viewtopic.php?f=49&t=91055](http://forums.linuxmint.com/viewtopic.php?f=49&t=91055)

Hope it helps you :D

---

### Post by Hipster Doofus on 2012-01-09
When I get there it says to download the file ending with ".deb". 

All that is there are these two:

[LIST]
[*]       [dkms-hda_0.201201092054~oneiric1.dsc]("https://code.launchpad.net/%7Eubuntu-audio-dev/+archive/alsa-daily/+files/dkms-hda_0.201201092054%7Eoneiric1.dsc")          (662 bytes)
[*]       [dkms-hda_0.201201092054~oneiric1.tar.gz]("https://code.launchpad.net/%7Eubuntu-audio-dev/+archive/alsa-daily/+files/dkms-hda_0.201201092054%7Eoneiric1.tar.gz")          (314.1 KiB)
[/LIST]


Any clue as to which one? I suppose it is the .dsc?

---

### Post by Hipster Doofus on 2012-01-09
Thanks for the help.

I give up. All morning trying to sort this out. End up with no sound.
Will give some other distro a go.

---

