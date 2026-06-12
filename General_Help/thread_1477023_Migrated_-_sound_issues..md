---
title: "Migrated - sound issues."
date: 2010-05-08
forum: General Help
---

### Post by ZazzyE on 2010-05-08
Hi, I'm new.  I'm not even sure which thread to post this under!

I'm  just moved to lubuntu 10.04 from an old distro lxde that was hacked  together and didn't work well.  My sound has this horrible feedback!   Its quiet but constant.  Whenever I move the mouse/touchpad or when  pages download from the internet, the feedback changes to a grinding  sound.  Muting the Mic channel in pulseaudio's device selector helps,  but doesn't fix it all the way.  I can play sound, even get it to  record, but this quiet, maddening feedback is always there.

   I've installed and removed pulseaudio and oss, recompiled alsa... played  with pulseaudio and the alsamixer like threads here suggest....  nothing.  It just changes the feedback.

Using a usb wireless  adapter in place of the internal nic only changes the feedback from  loading a webpage.  It is quieter, but its still there.

The worst  part is, I just switched after I got my motherboard replaced.  I'm  running a Dell D-830, onboard sound, video, wireless, etc.  The old  motherboard melted the videocard after 2 years of running with a piece  of tape that dell left between the heatsync and the videocard's putty.  

If  it turns out to be hardware, I'll need to be able to prove it - and I  couldn't get sound working at all on the old distro.

It would be nice to use the mic in tinychat, but I'll wait on trying to pull the sword from that stone until I've got the rest working.

---

### Post by dino99 on 2010-05-08
goto synaptic and install: paprefs and gnome-alsamixer (tweak it as you need)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lidex on 2010-05-08
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

Now can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by ZazzyE on 2010-05-11
You know how different distributions sometimes have different options?  Well, I've tried enough distos to be convinced that no linux distribution will do it automatically.   Funnything is, the distro I was using before didn't have these problems - now, it does.


dino99 - thanks, but that just ended up giving me a new interface to what I've already tweaked.

lidex - 
uname -a
Linux 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 

aplay -1
*** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asoud/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

head -n 1 /proc/asound/card*/code#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9205

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

---

### Post by ZazzyE on 2010-05-17
Turns out it was a hardware issue.  Got that handled.  Next up, getting the mic to work on tinychat.

---

