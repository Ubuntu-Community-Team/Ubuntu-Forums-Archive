---
title: "Already tried the sticky [Sound Problems] Sony Vaio VPCYB15AG"
date: 2011-03-05
forum: General Help
---

### Post by gotamangoflavouredrat on 2011-03-05
Went through the steps in the sticky [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) & [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/537448/comments/102](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/537448/comments/102)

**cat /proc/asound/version**
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Feb  1 2011 for kernel 2.6.32-29-generic (SMP)
```

All levels in the sound panel are at _MAX_ volume, _nothing_ including the microphone are "muted"
[B]
aplay -l[/B]
```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**lspci | grep -i audio**
```
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

```
[B]
cat /proc/asound/card0/codec#* | grep Codec[/B]
```
Codec: ATI R6xx HDMI

```

Tried this as well [http://ubuntuforums.org/showpost.php?p=10309974&postcount=4](http://ubuntuforums.org/showpost.php?p=10309974&postcount=4)
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
-------------------------
Results from Alsa-project.org
[http://www.alsa-project.org/db/?f=35510c86b2a8a67f75b1e20e56524e3c690fccf8](http://www.alsa-project.org/db/?f=35510c86b2a8a67f75b1e20e56524e3c690fccf8)

```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Mar  5 11:52:31 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCYB15AG
Product Version:   C9007E4U


!!Kernel Information
!!------------------

Kernel release:    2.6.32-29-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


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

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0x90244000 irq 27
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x90240000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:01.1 0403: 1002:1314
	Subsystem: 104d:9082
--
00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 104d:9082


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

```

**So what gives? The last laptop was an LG, 9.10 installed seamlessly, does sony **really put strange components in its machine?

Thanks in advance to everyone reading this , hoping for a solution.

---

### Post by gotamangoflavouredrat on 2011-03-05
err forgot to post the problem:

**No audio :(**

However , in the sound control panel the microphone seems to be working. The sound sensitivity indicator moves when the laptop is tapped

---

### Post by gotamangoflavouredrat on 2011-03-10
Shameless Bump
[IMG]http://i54.tinypic.com/2rdu6bs.jpg[/IMG]

---

### Post by arpitj on 2011-03-24
Any body with a solution or an idea that might work?

I too have the exact same problem.

---

