---
title: "Headphones and Speakers Work With Pulse Audio"
date: 2010-08-12
forum: General Help
---

### Post by oscargodson on 2010-08-12
If I have pulse audio installed and i go to Output Devices and change the Port from Analog Speakers to Analog Output or Analog Headphones my headphones play and not the speakers, however, if i uninstall pulse i can't change this. Also, when pulse is not running headphones AND speakers play sound, and lastly, and the most annoyingly, even if i do have pulse running the entire time and i unplug my headphones or plug them in i have to manually change it to where I want it to play. I also tried adding:

```
options snd-hda-intel model="olpc-xo-1_5"
```

to the end of /etc/modprobe.conf/alsa-base.conf

I have a ThinkPad L512 and get this:
```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX
```

for codecs. So, please, any suggestions?

---

