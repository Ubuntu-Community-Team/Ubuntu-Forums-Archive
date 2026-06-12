---
title: "Sound problem in UBUNTU 10.04.2"
date: 2011-08-13
forum: General Help
---

### Post by Pranaya on 2011-08-13
I am new to LINUX and I have installed UBUNTU last month. Every thing is fine but no sound.
I tried to solve the problem as per UBUNTU documentation but still not succeed.
Please any one help me.
I am new to linux and to this forum too. So please help me.

Below is my alsa information script
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Aug 13 05:32:32 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      G31M-ES2L
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.32-32-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22


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

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 1458:a002


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_utf8
isofs
binfmt_misc
ppdev
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
i915
drm_kms_helper
psmouse
serio_raw
intel_agp
atl1c
drm
i2c_algo_bit
video
output
agpgart
lp
parport
floppy


!!ALSA/HDA dmesg
!!------------------

---

### Post by lmarmisa on 2011-08-13
Your audio controller seems an Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01). According to the Ubuntu documentation this controller is supported by your version of Ubuntu:

[http://www.ubuntu.com/certification/catalog/component/pci:27D8:8086-AUDIO](http://www.ubuntu.com/certification/catalog/component/pci:27D8:8086-AUDIO)

But the ALSA script does not recognize your device.

I would like to confirm if you audio controller is recognized by Ubuntu. Open a terminal, type this command and post the result:

```

sudo lshw -C multimedia

```

I have found this other link that could help you:

[http://ubuntuforums.org/archive/index.php/t-1467387.html](http://ubuntuforums.org/archive/index.php/t-1467387.html)

---

### Post by Pranaya on 2011-08-13
> **lmarmisa said:**
> Your audio controller seems an Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01). According to the Ubuntu documentation this controller is supported by your version of Ubuntu:

[http://www.ubuntu.com/certification/catalog/component/pci:27D8:8086-AUDIO](http://www.ubuntu.com/certification/catalog/component/pci:27D8:8086-AUDIO)

But the ALSA script does not recognize your device.

I would like to confirm if you audio controller is recognized by Ubuntu. Open a terminal, type this command and post the result:

```

sudo lshw -C multimedia

```I have found this other link that could help you:

[http://ubuntuforums.org/archive/index.php/t-1467387.html](http://ubuntuforums.org/archive/index.php/t-1467387.html)

Thanks for responding so quick.
This are the result of the code you send to me.
*-multimedia UNCLAIMED  
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fdff8000-fdffbfff

---

