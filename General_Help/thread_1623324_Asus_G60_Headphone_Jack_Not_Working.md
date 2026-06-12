---
title: "Asus G60 Headphone Jack Not Working"
date: 2010-11-16
forum: General Help
---

### Post by pedal2themedal on 2010-11-16
I have an Asus G60vx notebook and when I updated to 10.10 I lost audio through my headphones. The speakers work fine, just not the headphones. 

Normally I am able to sole these things on my own through searching forums and what not, but no solutions I have found work for me so far.

Things I have tried:
1. Make sure the latest drivers are installed according to the above, then edit the file /etc/modprobe.d/alsa-base.conf
and add the following line:
options snd-hda-intel model=dell-laptop
Reboot and test. Other models to test are:
thinkpad
ideapad
hp_laptop
dell-vostro
olpc-xo-1_5
2. Checking on the alsamixer thru the terminal. Headphones is green, but there is only the 00 notch, like there is no volume to change.
3. Updating my alsa files via synaptics, my kernel model is 2.6.35-23-generic. There is no alsa drivers for this kernel that I can find yet, however I found this, Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots. Installed it still doesnt work.


Here is the link to my bug file: [http://www.alsa-project.org/db/?f=8d6cd60ac90c0ed5935396c25709db7a22e10c5a](http://www.alsa-project.org/db/?f=8d6cd60ac90c0ed5935396c25709db7a22e10c5a)


Thanks, Robert

---

### Post by pedal2themedal on 2010-11-16
I also forgot to mention that my sound preferences arent working. When I click on the volume in the  taskbar, and them click sound preferences, it does not pull it up.

---

