---
title: "sound issues in Karmic Koala"
date: 2009-11-13
forum: General Help
---

### Post by petru.marginean on 2009-11-13
Hi,

I have sound issues.
After rebooting the machine the sound works fine.
After awhile (I do not know why/when this happens) the sound doesn't work any more.
This sequence brings back the sound:

```
$> sudo /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                 [ OK ]

$> rm -rf ~/alsa* ~/.pulse*

$> sudo rm -rf ~/alsa* ~/.pulse*

$> sudo alsa force-reload
Unloading ALSA sound driver modules: snd-seq-dummy...
Loading ALSA sound driver modules: snd-seq-dummy...

$> sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...                                        [ OK ] 
```How can I solve the problem? (instead of fighting with the effects)

I noticed this in the log:

```
$> egrep -i "error" < /var/log/messages | grep audio
Nov 13 17:52:10 ubuntu kernel: [81900.461933] pulseaudio[14308]: segfault at 4a45a0 ip 004a45a0 sp bfc2c38c error 4 in libwrap.so.0.7.6[4f2000+7000]
Nov 13 18:04:32 ubuntu kernel: [82642.538191] pulseaudio[19102]: segfault at 2065e0 ip 002065e0 sp bfd6293c error 4 in libxcb.so.1.1.0[22b000+1c000]

```This is some information about my machine:

```
$> lsb_release -a && uname -r 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
2.6.31-14-generic

$> sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/petrum not ours.
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$> cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22

$> lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)


```Regards,
Petru

---

### Post by petru.marginean on 2012-07-17
I use 12.04 now and this works fine.

---

