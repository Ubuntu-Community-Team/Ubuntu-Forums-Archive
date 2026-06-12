---
title: "sound problem"
date: 2012-02-21
forum: General Help
---

### Post by kalyan g on 2012-02-21
hi,
I am running Ubuntu 11.10( upgraded from11) on my pc.I have creative sound card ca0106 on my board. 
My problem is my sound card is not working properly on ubuntu. it is working well on windows. I followed sound troubleshooting procedure to fix it. when i follow the procedure step1([https://help.ubuntu.com/community/SoundTroubleshootingProcedure)sound](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)sound) card is working well but when i reboot system I am facing the same problem again.Some times even after following the step1 i am unable to fix the problem. When i reboot the system ALSA is not active message is showing.what should i do? can you any one help me please.. 
This is my system info.
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Thu Feb 16 10:06:02 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:              
Product Name:              
Product Version:           


!!Kernel Information
!!------------------

Kernel release:    3.0.0-16-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

04:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

04:01.0 0401: 1102:0007
	Subsystem: 1102:1004


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
crc_ccitt
rfcomm
bnep
bluetooth
oss_usb
oss_audigyls
osscore
binfmt_misc
i915
drm_kms_helper
drm
psmouse
i2c_algo_bit
cdc_wdm
ppdev
video
cdc_acm
cdc_ether
usbnet
parport_pc
serio_raw
lp
parport
floppy
r8169


!!ALSA/HDA dmesg
!!------------------



</pre></body></html>

---

### Post by zero2xiii on 2012-02-21
Hay,

Just a poke in the dark, but it seems your issue might be:

> ESound Daemon:
 Installed - Yes (/usr/bin/esd)
** Running - No**

I had a similar soundcard and had similar issues, I however upgraded my system and got a realtech card and havent had the problems since.

Try starting the daemon manualy and see if it works, if it works, add a line to a startup script to activate it everytime you boot.

Cherz

---

