---
title: "alsa-base.conf content for HP Pavilion dv6"
date: 2012-06-16
forum: General Help
---

### Post by nifhel on 2012-06-16
Hi,

could someone with a HP Pavilion dv6 post the full content of his "/etc/modprobe.d/alsa-base.conf" please ? 

I got an update 3 days ago and my audio stopped working. Then I added "options snd-hda-intel model=auto" and i got my audio working again, but the microphone is not working, and the headphones don't mute the speakers!

Before the update everything was working great! And also from a live USB of kubuntu everything is working .

My hardware configuration is this: [http://goo.gl/tptnX](http://goo.gl/tptnX) 

My **aplay -l** is: 
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: SB [HDA ATI SB], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: SB [HDA ATI SB], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

Thankyou.

---

### Post by nifhel on 2012-06-16
if I add this at the end of /etc/modprobe.d/alsa-base.conf I get my microphone and my headphones working, but the speakers are not: 

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=1

if I add this instead the speakers work, but when I plug the headphones the speakers don't mute:

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=1

**This is so annoying!! **

---

### Post by nifhel on 2012-06-16
My alsa information are at 
[http://www.alsa-project.org/db/?f=a62f36f0949e4bc1aa49a258ca189bcbe75c6013](http://www.alsa-project.org/db/?f=a62f36f0949e4bc1aa49a258ca189bcbe75c6013)

---

