---
title: "pulse audio issues"
date: 2010-05-07
forum: General Help
---

### Post by hanlin on 2010-05-07
I have a Dell Inspiron 9400 that I just installed Lucid on. However, I have some issues with the sound. It works fine in that I can hear sounds. However, increasing the volume using the icon doesn't actually increase the volume. Instead, it makes it sound a little differently (sounds like treble is increased as volume is "increased"). The only way to actually control the volume is to do it through the applications tab. Any idea what's going on?

---

### Post by coolcaseley67 on 2010-05-07
hi 

how did you install 10.04 ???

---

### Post by hanlin on 2010-05-07
Fresh install.

---

### Post by hanlin on 2010-05-07
So I installed GNOME Alsa Mixer. It turns out that the PCM slider actually controls the volume, whereas the Master slider just changes the way it sounds. Is there a way to switch the behavior of the sliders?

---

### Post by lidex on 2010-05-08
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by hanlin on 2010-05-08
This is an Insprion 9400 laptop.

> 
-$ uname -a
Linux olga-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

~$ head -n 1 /proc/asound/card0/codec#0
Codec: SigmaTel STAC9200


---

### Post by dino99 on 2010-05-08
may need to install paprefs

---

### Post by lidex on 2010-05-08
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` 

Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m27 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by hanlin on 2010-05-08
Neither of those worked. I'm still having the same issue.

---

### Post by lidex on 2010-05-08
Did you reboot?
What is the output of this:
```
cat /etc/modprobe.d/alsa-base.conf
```
Try gnome-alsamixer and enable everything in 'Edit>Sound Card Properties'

---

### Post by hanlin on 2010-05-09
> 
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
options snd-hda-intel model=dell-m27


Yes, I rebooted. Everything in gnome-alsamixer is enabled. What exactly is PCM supposed to control?

---

### Post by hanlin on 2010-05-10
I ran across this workaround today:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies")

---

### Post by lidex on 2010-05-11
More alsa-base.conf options:
```
options snd-hda-intel model=dell
options snd-hda-intel model=dell-bios
options snd-hda-intel model=dell-3stack
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel model=dell-eq
```

---

