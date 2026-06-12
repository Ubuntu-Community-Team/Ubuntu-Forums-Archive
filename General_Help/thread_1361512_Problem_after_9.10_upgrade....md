---
title: "Problem after 9.10 upgrade..."
date: 2009-12-22
forum: General Help
---

### Post by ninja senses on 2009-12-22
So far I have a couple of major problems, I think they are all related to drivers.  First off I have no sound, I went through all the threads here with no luck:

  *-multimedia            
       description: Audio device
       product: Radeon HD 3870 Audio device
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:f1010000-f1013fff
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f7000000-f7003fff

looks liek i have two choices and I dont care which is better but I need sound.  and I have gone through the threads with no luck getting them.  It obviously recognixes the cards but not sound!!(yea i do no not have mute checked.)

I also noticed really slow graphics(I think cause no graphics card driver.)  I tried to authenticate the driver in the administration options but no luck.  and lastly I realize I have the ii  linux-image-2.6.31-16-generic              2.6.31-16.53    kernal but it is not running, how can I get this one going?

---

### Post by mac666 on 2009-12-22
What connection do you use?
SPDIF, Analog?

have you tried upgradring alsa? Check the alsa upgrade script (google it)
Have you tried to select it in alsaconf?
Run alsaconf in term

---

### Post by ninja senses on 2009-12-23
> **mac666 said:**
> What connection do you use?
SPDIF, Analog?

have you tried upgradring alsa? Check the alsa upgrade script (google it)
Have you tried to select it in alsaconf?
Run alsaconf in term

I just tried running the alsa upgrade script and I still have no sound unfortunately.   Also how can I figure out what connection I use?  aplay -l shows no cards

cat /proc/asound/version shows Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

alsaconf returns :

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
options snd-hda-intel power_save=10 power_save_controller=N

---

### Post by ninja senses on 2009-12-23
I figured i should also mention when i upgraded i chose to keep all the menu.lst's the same

---

### Post by ninja senses on 2009-12-23
I fixed the sound problem, the problem was that i was not using the newest kernal, as soon as i changed my menu.lst to incorporate the new kernal and boot from it, the sounds problem was fixed.  It seems as if my video card is still not working correctly though

---

