---
title: "No Onboard Sound (Ubuntu 10.10)"
date: 2010-11-09
forum: General Help
---

### Post by Akiva on 2010-11-09
Hi Everyone,
I recently installed Ubuntu 10.10 on my Sony Vaio VPCEE2E1E. I've been able to avoid any major problems, however, my onboard sound doesn't work. I've tried plugging speakers into the laptop and this works perfectly. I'm rather confused as to why the onboard sound isn't working though.

Here's the output for lspci on my machine:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
aled@blaze:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Sony Corporation Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
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
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

And lsusb:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0186 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0408:03f5 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any help with this would be greatly appreciated.

---

### Post by Ashrael on 2010-11-10
HI!

I use 10.04 still but I think it's about the same in 10.10..

I've had this too some time ago...and...it is really simple to solve..
If you go to SYSTEM>PREFERENCES>SOUND, you can there choose your speaker setup...you may have to try several before succes is achieved...Of course do this WITHOUT any external speakers attached.


HTH!

---

### Post by dino99 on 2010-11-10
otherwise install alsamixer from synaptic, and set your prefs

---

### Post by Ashrael on 2010-11-10
YES! you are right Dino! I totaly forgot about that!

---

### Post by blueridgedog on 2010-11-10
> **Akiva said:**
> Hi Everyone,
I recently installed Ubuntu 10.10 on my Sony Vaio VPCEE2E1E. I've been able to avoid any major problems, however, my onboard sound doesn't work. I've tried plugging speakers into the laptop and this works perfectly.

Which means your onboard sound system is working, but your build in speakers are probably muted.  Install alsamixer (installed by default now no?) as suggested, run it from a terminal with the command:

```
alsamixer
```

Then look for any item that is muted.  It will have "MM" in the volume figure.  Arrow over to the item and press "M" to un-mute then arrow up to increase the volume.

---

### Post by iSeizmik on 2011-03-29
I've tried all these methods and I know they should work, they just don't. I've been put off using Ubuntu for a while now because of it(since the release of 10.04).

I've ramped all the volumes in alsamixer up to 100 and the preferences in the sound menu, open up Rhythmbox(I've also tried by watching youtube videos in Firefox) and I get nothing. Only thing that can be said is that when I use the terminal-run alsamixer and go from zero to one hundred quickly I can hear the speaker crackle a little because the volume is increasing in one's instead of just zero then one hundred.. That may sound stupid but at least I know the speakers are being acknowledged.

I suppose I'll try updating to 10.10 and see if that helps; in the mean time, any ideas?

---

### Post by blueridgedog on 2011-03-29
Did you double and triple check for "MM" indicating that they were muted?  I have seen this many times.

---

### Post by iSeizmik on 2011-04-13
> **blueridgedog said:**
> Did you double and triple check for "MM" indicating that they were muted?  I have seen this many times.

Yes, I've done this, I've also tried finding drivers for my sound card, but they are up to date.

---

### Post by Ashrael on 2011-06-01
Hi blueridgedog, just posting to check if you have solved this problem already?

greetings!

---

### Post by blueridgedog on 2011-06-01
My issue was that it was muted, however the original poster seems to have had another issue.

---

