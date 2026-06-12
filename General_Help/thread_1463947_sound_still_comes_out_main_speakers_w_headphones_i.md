---
title: "sound still comes out main speakers w/ headphones in"
date: 2010-04-27
forum: General Help
---

### Post by skelooth on 2010-04-27
Hello, running Lucid.

When running rythmbox today I noticed that when my headphones are plugged in sound still comes out of my main speakers, just much much lower.

Ideas? I don't even...

---

### Post by lidex on 2010-04-27
That's actually pretty common. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by skelooth on 2010-04-28
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pavella@pavella:~/Desktop$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

It's a Gateway DX series tower, but I can't seem to find a model number for it.

---

### Post by dino99 on 2010-04-28
tweak the settings with gnome-alsamixer

---

### Post by LurkyLou on 2010-04-28
I've had a lot of success with similar issues using 'pavucontrol', the pulseaudio volume control.  You can get it via Synaptic.

---

### Post by lidex on 2010-04-28
Try this. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by Julita on 2010-05-01
**EDIT: SOLVED!**

Hi! Strange thing is - the sound goes from the speakers of my netbook with headphones plugged in only on one site! Everywhere else, on Youtube, e.g., everything is fine, using the same Flash plugin. I have removed Pulseaudio because it wouldn't work with my microphone in Skype, so System->Preferences->Sound is not an option in my case. I have adjusted everything possible in alsamixer. I have no clue what makes this particular site so special; in previous Ubuntu release, that was never an issue. This is so weird... I visit tons of sites every day, but only this particular one causes the sound to play both from headphones and speakers... In Mandriva (Gnome), I could install gmixer for sound control; in Ubuntu, however, there is no such package. I would welcome very much any suggestions :)

EDIT: It seems the problem has spread to the files on my computer! Honestly today everything was fine! And I haven't rebooted the system... Or removed any sound-related software. OK, I have solved the issue by muting "speakers" in alsamixer :)

---

