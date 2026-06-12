---
title: "Fresh Ubuntu 9.10 | No Sound"
date: 2010-04-29
forum: General Help
---

### Post by schoft on 2010-04-29
Hey, i'm experiencing the lack of sound on my Asus P5W DH Deluxe motherboard. It has an integrated sound card. It worked out of the box with the BackTrack 4 LiveCD ! What can i do to solve this :confused: It doesn't even regonize a hardware card. Maybe a bios problem....

ubuntu 9.10 x64

---

### Post by schoft on 2010-04-29
It was indeed a Bios problem. I needed to disable the sound settings from "VISTA" to "non-vista" somewhere in the bios. For everyone that has a P5W DH DELUXE, that helps.

---

### Post by dino99 on 2010-04-29
> **schoft said:**
> Hey, i'm experiencing the lack of sound on my Asus P5W DH Deluxe motherboard. It has an integrated sound card. It worked out of the box with the BackTrack 4 LiveCD ! What can i do to solve this :confused: It doesn't even regonize a hardware card. Maybe a bios problem....

ubuntu 9.10 x64

maybe i can help you as i have the same MB and have had the same issues some weeks ago. 

sudo gedit /etc/modprobe.d/alsa-base.conf

at the end i've added these 2 lines:

options snd-hda-intel model=auto

options snd-hda-intel model=6stack-dig

dont remember if reboot is required or not, but goto system-pref-sound to see if its recognized. Then install gnome-alsamixer and paprefs if not. Tweak the settings into gnome-alsamixer.

---

### Post by garvinrick4 on 2010-04-29
[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by schoft on 2010-04-29
Thanks guys, solved it.

---

### Post by dino99 on 2010-04-29
glad to help you, could you goto thread tools on top and mark it as "solved"

---

