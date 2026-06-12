---
title: "No sound"
date: 2009-12-10
forum: General Help
---

### Post by Xbehave on 2009-12-10
So i played about with 2.6.32 and got sound working but have now loust didn't have sound however now i've lost sound in my old kernel with the same issue:
[http://www.alsa-project.org/db/?f=9b5a31c8a78a308e620798261b8feafdb6521e08](http://www.alsa-project.org/db/?f=9b5a31c8a78a308e620798261b8feafdb6521e08)

With enhanced debugging from my 2.6.32 i think the problem is that the drivers is being loaded wrong, perhaps it's a mistake in 

/etc/modprobe.d/alsa-base.conf
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
options snd-hda-intel power_save=10 power_save_controller=N
```
how would i reset it to defaults?

**edit**: i used
dpkg -S /etc/modprobe.d/alsa-base.conf
> alsa-base: /etc/modprobe.d/alsa-base.conf 
sudo aptitude pruge alsa-base
sudo aptitude install alsa-base
to restore the original config

---

### Post by Xbehave on 2009-12-11
```
speaker-test

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory
```

```
[    5.101980] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave Headphone Playback Volume, skipped
[    5.101990] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave Speaker Playback Volume, skipped
[    5.101993] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave Mono Playback Volume, skipped
[    5.101996] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave Line-Out Playback Volume, skipped
[    5.101999] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave PCM Playback Volume, skipped
[    5.102035] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave Speaker Playback Switch, skipped
[    5.102038] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave Mono Playback Switch, skipped
[    5.102040] ALSA sound/pci/hda/hda_codec.c:1658: Cannot find slave IEC958 Playback Switch, skipped
```
I'm getting the same problem on the mainline ppa and with alsa-lib 1.0.21/1.0.20

---

### Post by Xbehave on 2009-12-12
Ok so i went away to suse then came reinstalled ubuntu, everything works but on my custom kernel i get no sound as a user (as root everything is fine)

```
speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:975:(snd_pcm_dmix_open) unable to create IPC semaphore
Playback open error: -13,Permission denied

```

---

### Post by Xbehave on 2009-12-12
added my self to audio group now all is good! :D

---

