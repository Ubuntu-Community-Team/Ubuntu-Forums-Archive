---
title: "Sound stopped working after Karmic upgrade"
date: 2009-10-30
forum: General Help
---

### Post by Cuddles McKitten on 2009-10-30
Now that Karmic's out of the beta, I don't think I can keep hoping for some fix from an update anymore.  My problem is that ever since upgrading to Karmic in early October, I've had to run a little script after GNOME loads up:

```

#!/bin/bash

rm -r ~/.pulse
killall pulseaudio
sudo alsa force-reload
```If I don't run that, my sound won't work.  I have absolutely no idea what to do to fix whatever it causing the problem.

Here's the relevant information in my lspci -v
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0806
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```And just in case, here's my alsa-base.conf
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel model=auto power_save=10 power-save-controller=N

```

---

### Post by OlorinIWas on 2009-10-30
yeah..my sound broke as well...using audigy2 zs

wondering if this can be resolved Jaunty style via multip sound solut. manual?...

---

### Post by bezolaam on 2009-10-30
> **OlorinIWas said:**
> yeah..my sound broke as well...using audigy2 zs

wondering if this can be resolved Jaunty style via multip sound solut. manual?...


I have the same problem with audigy2 zs. Only onboard soundcard is working after upgrade to carmic  :(:(:(

---

### Post by OlorinIWas on 2009-10-30
getting p.a. device chooser w/applet, sound, and p.a. prefs on the same page worked getting my multi channel sound back..

..but alsa seems confused as to what mixer it is running and how to mix correctly.

---

### Post by Korrode on 2009-10-31
> **bezolaam said:**
> I have the same problem with audigy2 zs. Only onboard soundcard is working after upgrade to carmic  :(:(:(

I have an early Audigy and also am having problems.
Firstly i'll note; i used the 'alternate' CD and did a 'command line only' install, then installed xorg, openbox, alsa-base, etc.

Applications running in X don't seem to be able to talk to ALSA.

eg.
If i run alsamixer from bash when i've first booted, it's fine.
Whilst i'm running X, if i hit ctrl+alt+F2 and goto that console and run alsamixer, it's fine.
If i run alsamixer in a terminal within my X session, i get:```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

I've tried reloading ALSA while X is running```
:~$ sudo alsa force-reload
```
...and it unloads and reloads fine, but doesn't help my problem.

I also tried using module-assistant to build my own alsa kernel module using the alsa-source package... didn't help.

Considering ALSA is working fine outside of X, i can only assume X itself, or maybe some new "protect the user from themself" technology is the cause.

Any help would be greatly appreciated :(

For the last ~year i ran Debian Testing, but decided the benefits of a 'rolling-distro' were being out-weighed by the downfalls, so with the release of Karmic i've come back to Ubuntu, and so far i'm really happy and impressed, but this sound issue is kicking my ***. :P

---

### Post by Korrode on 2009-10-31
Well i've now fixed it...

My mind can't understand the logic of it, but the solution ended up being simple; I added myself to the 'audio' group.

Usually this would've been one of the first things i'd check, but i figured it couldn't be that because my user account could use ALSA from a console just fine.

Weird.

---

### Post by mebigfatguy on 2009-10-31
> **OlorinIWas said:**
> yeah..my sound broke as well...using audigy2 zs

wondering if this can be resolved Jaunty style via multip sound solut. manual?...


i also have an audigy 2 that doesn't work even with fresh install.

---

