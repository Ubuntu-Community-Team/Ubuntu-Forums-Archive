---
title: "Ubuntu No Sound detected + waiting for sound to be detected"
date: 2011-08-16
forum: General Help
---

### Post by virenegi on 2011-08-16
Hello there,
           I have installed Ubuntu 10.04 32 bit LTS on my Dell 15R(64bit) laptop
ever since I installed above Ubuntu I'm facing sound Problem as in there is no sound detected google followed ever thread did ever thing that was mention in the thread with no result  and finally it has brought me to write this  hread 
 Please guys(Ubuntu geeks) please help me out on this . The issue just eating and playing in my head 24x7 
 here are the few output of command that that found on various thread that might the ultimate ubuntu geek genuinely trying to help me out

COMMAND :- 
** lspci **

 00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4b (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
09:00.0 Network controller: Intel Corporation Device 008a (rev 34)
0b:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)


**aplay -l **

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Please guys Help me on this

---

### Post by gordintoronto on 2011-08-16
If there is a single improvement from 10.04 to 11.04, it is sound. Try running a LiveCD of 11.04. Also, search Sound Preferences for something being muted.

---

