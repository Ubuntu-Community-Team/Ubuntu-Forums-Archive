---
title: "pulseaudio + alsa = choppy sounds, getDMAPos error - help deal with sound issues"
date: 2010-01-20
forum: General Help
---

### Post by suzenon on 2010-01-20
Hello. 
I'm having issues with (what i think it is) alsa and pulse audio mixing each other. I'm not advanced user or something so i can't figure out how to deal with my ubuntu sound issues.
When i first installed ubuntu i could only play one sound source at a time. I've uninstalled pulseaudio, updated ALSA and it was fine.

But i've found pulseaudio is required for Mangler - great ventrilo client i'm using.
So... i've installed pulseaudio using this guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) everything went smooth, but after some time i've noticed that sound is still not ok. 

When my OS is up for a longer time (few hours at least), when i start a movie i get some choppy sounds. I've tried to change sound source in my player of choice (VLC) but without any effect. This problem doesn't appear always.

Also i'm having similar issues when playing quake live. I get this error but don't really know what does it mean - you can see it in attachment.

Here are some infos:
```

cat /proc/asound/modules
 0 snd_hda_intel


aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: ALC888 Analog [ALC888 Analog]
  Urz&#261;dzenia podrz&#281;dne: 0/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: Intel [HDA Intel], urz&#261;dzenie 1: ALC888 Digital [ALC888 Digital]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0


cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.


lshw -C Multimedia
WARNING: you should run this program as super-user.
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
       resources: irq:22 memory:fb000000-fb003fff
```I'll be gratefull for any clues what could be wrong, also tell me if i should provide any more infos.

EDIT: damn... i'm bind, forgive me my noobness, the answer was right here, it's darkest under the lamp (or something like that...)

[http://ubuntuforums.org/showthread.php?p=7505646#post7505646](http://ubuntuforums.org/showthread.php?p=7505646#post7505646)

EDIT2: eeeh... i was happy too early :(

---

### Post by suzenon on 2010-01-20
Bumping topic, it's not resolved i was happy too early. :( 
Making this .asoundrc script form link above did resolved choppy sound problem, BUT different problem appears, only one sound output source at a time. So this means i can't play quake and use mangler at same time. In fact i guess i won't be able to watch video on yt if i've paused movie (or any sound source) in player of choice as it was before.

Any clues how could i fix it? Maybe adjusting something in this script file?

---

