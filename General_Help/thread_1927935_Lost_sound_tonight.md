---
title: "Lost sound tonight"
date: 2012-02-19
forum: General Help
---

### Post by HeroOfCanton on 2012-02-19
No new hardware. No new software. Sound just disappeared on me...

To get headphones working on this system was a PITA in the first place. Took me at least 8 hours of GIS + trial and error to finally find an alsa-base configuration that worked properly. Been up and running just fine for months though. Now, out of nowhere, ALL sound is gone. Online/local videos, games, etc. Even through the on-board speakers. Nothing...

Only thing I can think of is an update killed something. Booted to  Windoze and sound kicked right up on the login screen, so it's not the  card.
 
Any ideas???

```

rev@revs-lt:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: SigmaTel STAC9205
rev@revs-lt:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
rev@revs-lt:~$ 

```

(Please help so I don't have to go back to Windoze!!! I've proudly moved all of my java/droid development to Ubuntu XFCE but can't work with no sound. This would be a killer for me.)

---

### Post by HeroOfCanton on 2012-02-19
*bump

Anyone? Bueller? Bueller?

---

### Post by HeroOfCanton on 2012-02-19
Was using Ubuntu with the XFCE shell so I decided to just reinstall with a proper xubuntu distro. Did all of my updates and seem to be okay for now. Hopefully it holds up.

I'll stop talking to myself now. :D

---

### Post by mardybear on 2012-02-20
> **HeroOfCanton said:**
> Was using Ubuntu with the XFCE shell so I decided to just reinstall with a proper xubuntu distro. Did all of my updates and seem to be okay for now. Hopefully it holds up.

I'll stop talking to myself now. :D
Hi HeroOfCanton.

Good to hear you got things running.

Sounds like a Windows solution - when something breaks reinstall the entire operating system ;)

mardybear

---

