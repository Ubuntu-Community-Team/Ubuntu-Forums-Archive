---
title: "Quiet sound from speakers in Ubuntu 10.04 LTS"
date: 2010-05-12
forum: General Help
---

### Post by ChadBargo on 2010-05-12
Okay,so I installed Ubuntu 10.04 and while everything is working great except the sound. I have an ASUS P5lp-le motherboard that has onboard 5.1 audio,but my speakers are really quiet. I have tried running "alsamixer" in the terminal and everything was turned up all the way. Is there thing else I could try?

---

### Post by lidex on 2010-05-12
Check 'System>Preferences>Sound' as well as Pulseaudio Volume Control. You may want to install gnome-alsamixer if not on your system as well.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get install pavucontrol
```
```
sudo apt-get install gnome-alsamixer
```

---

### Post by ChadBargo on 2010-05-13
i tried both of those with no luck,i  guess i'll have to shop for a cheap sound blaster card off of ebay. thanks anyway though

---

### Post by lidex on 2010-05-13
That was generic first step. More info would help. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by uviathon on 2010-05-14
I'd appreciate some help as well.  Really only regularly used Ubuntu on my netbook before (used Mint for a brief time on my desktop, but it was a while back).  I have a logitech 5.1 setup.  On this machine, it's going through the 3 analog jacks (my other machine uses optical).  I get sound ok through center and fronts, but sub seems low, and rears get no sound.  

Here's the output of the terminal commands requested: 

_uname a_
```
Linux unit0 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```


_aplay -l_
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

_cat /proc/asound/version_
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```


_head -n 1 /proc/asound/card*/codec#*_
```
Codec: Analog Devices AD1986A
```



I'm a tad lost, as I'm used to either the WindowsXP sound mixer, or the Creative one on my other machine.  I guess I really don't get why there are sooooo many sliders on these mixers, and none of them seem to adjust anything, except for muting if I check that box.  I realize it's not going to have the trueness of the optical.  I'm just looking for the comparable "fake" 5.1 output of my XP install.  

The only things I've tried so far are installing the following mixers through Synaptic: 

gnome-alsamixer
qamix
gamix


This PC is one I built.  
* Athlon64 3000
* 3GB RAM
* 450GB partition of a WD 650 Black
* Asus A8N-VM mobo, and I'm using the onboard sound
* MSI GeForce 7100GS

---

### Post by 2hot6ft2 on 2010-05-14
Maybe these will help.

[PulseAudio Fixes & System-Wide Equalizer Support]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=22")

[Make sound quality better in 2.5 Karmic]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=222")

:guitar:

---

### Post by razorboy5 on 2010-05-14
I've had the same problem in my old gateway laptop when i was running 9.10. Sound was topped in alsa but was rather soft (well less than what it was when running windows)

switching to OSS4 fixed this problem, maybe u wanna look into it :P rather a easy switch since there is a documentation with specific instructions

link if ur insterested :P

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by lidex on 2010-05-14
uviathon:
Try the alsa upgrade available through the link in my sig.

---

