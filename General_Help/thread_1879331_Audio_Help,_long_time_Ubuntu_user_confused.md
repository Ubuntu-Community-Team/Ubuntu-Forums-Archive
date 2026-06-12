---
title: "Audio Help, long time Ubuntu user confused"
date: 2011-11-11
forum: General Help
---

### Post by Landspeeder_95 on 2011-11-11
Good day Ubuntu community. 

I've used a number of iterations of Ubuntu in the past, and have installed it for many others (to move them away from windows into something more novice user proof).

This one has me floored.  I am in the process of building a full blown media / emulator arcade rig (to use XBMC).

1) I have NO audio over HDMI.  The onboard gpu is disabled in bios, I am using an NVIDIA card.  (please read below my aplay output).  How the heck to I switch the device from the bios disabled HDMI device to my nvidia card?

2) adding many new software items is NOT working (saying the ppa site is not found)... I.E. xbmc (I forced the install myself), mediabuntu, etc. It's like all of the [Oneiric Ocelot]("https://wiki.ubuntu.com/OneiricOcelot") repositories do not exist.  I have never had this problem in the past   

kemper@kemper-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
   Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
   Subdevices: 1/1
  Subdevice #0: subdevice #0

kemper@kemper-htpc:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

System Specs: 
  OS:  Most recent 32 bit build as of 11/07/2011
  Biostar TA785GE 128M (onboard GPU disabled in bios) 
  Nvidia GeForce GT430
  OCZ 30 GB Vertex SSD
  Samsung 2x1 GB PC2-6400 800Mbps DDR2 Very Low Profile 40nm class UDIMM
  AMD Athlon II X2 250 Processor

  Media storage on a network 'server'  (groan:  a Windows 7-64 machine).  

**Thank you greatly in advance!**

---

