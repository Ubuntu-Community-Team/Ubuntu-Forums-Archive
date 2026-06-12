---
title: "Fresh install of Lubuntu, no sound with USB headset?"
date: 2012-01-08
forum: General Help
---

### Post by yo2boy on 2012-01-08
Hi. I've just installed the LXDE distribution of Ubuntu and I'm liking it so far in terms of speed! But one thing that I can't get to work is audio with my HP USB headset.

I tried going into "Volume control" settings, but it's "grayed" out. Is there any hardware/driver information I can provide in order to solve this issue?

The same headset works fine in Xubuntu and Pinguy OS, it's just Lubuntu that it doesn't work in. 

(Side note: When I enter the command 'alsamixer' in terminal, it doesn't show my USB headset but my internal sound card, could this be the problem? )

---

### Post by afrodeity on 2012-04-13
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by ringo28 on 2012-05-13
hmmm, i have a hp4300workstation.. i can use my usb-headphone.., i started with xubuntu i looked for unity too test , and i use now  lubuntu :) , i have Pulseaudio-volume control in menu from sound and video menu. i change with a gues in de configuration menu..,  and other to digital..... that link i had it all in my synaptic why again?  i hope i could help :)

gr ringo

---

### Post by Rodney9 on 2012-05-13
```
sudo apt-get install pavucontrol
```

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

---

