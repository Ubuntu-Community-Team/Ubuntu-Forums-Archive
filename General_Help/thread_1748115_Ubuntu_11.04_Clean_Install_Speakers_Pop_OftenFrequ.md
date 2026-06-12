---
title: "Ubuntu 11.04 Clean Install Speakers Pop Often/Frequently"
date: 2011-05-03
forum: General Help
---

### Post by UnknownDiety on 2011-05-03
[http://ubuntuforums.org/showthread.php?t=1314834](http://ubuntuforums.org/showthread.php?t=1314834)

I tried to use that solution, but it didn't work because there was no "power_save" in there.

According to them the sound happens because the speakers are cutting off and on?

HP Pavillion dv6275us (dv6000 series)

---

### Post by RECKENEFIN on 2011-05-04
I'm having the same problem on my dv2000 with a clean 11.04.

Actually, the exact same problem, right down to the above referenced fix not working for the same reasons.

---

### Post by UnknownDiety on 2011-05-05
Hopefully someone will be able to help us then :P

---

### Post by hardyn on 2011-05-09
same, same

no solution though.

---

### Post by moragos on 2011-05-09
Same issue here.
I ran the following commands and the information is below:

uname -a
```
Linux shy-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```


aplay -l
```
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```


dpkg -l | grep "alsa"
```
ii  alsa-base                             1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-utils                            1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  bluez-alsa                            4.91-0ubuntu1                              Bluetooth ALSA support
ii  gstreamer0.10-alsa                    0.10.32-1ubuntu5                           GStreamer plugin for ALSA

```


head -n 1 /proc/asound/card*/codec#*
```
Codec: Conexant ID 5045

```


Any help would be greatly appreciated

---

### Post by dastrn on 2011-05-13
same issue for me. the old fix doesn't work anymore, as the power_save line is not in that alsa conf file.

Anyone find a fix to this?

---

### Post by jocefus on 2011-05-22
My speakers also pop every time they are initialized to play a sound. This didn't happen before when I was using Lucid on this old laptop.

Specs:
Inspiron 9300
Card: Intel ICH6
Chip: SigmaTel STAC9750,51

---

### Post by rojodojo on 2011-06-02
[I made a thread a few weeks back about this same problem]("http://ubuntuforums.org/showthread.php?p=10895842#post10895842").
This was a response I got,


> **wilhelmschumann said:**
> I have Upgraded some packages on My laptop ( HP Pavilion DV 9000 ) and that annoying popping noise has stopped .
 I think is something related with Xorg, Xorgserver or X11.

Cheers!

Those Packages updated are:


Upgraded the following packages:
apturl (0.4.2ubuntu5) to 0.4.2ubuntu5.1
apturl-common (0.4.2ubuntu5) to 0.4.2ubuntu5.1
firefox (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
firefox-gnome-support (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
flashplugin-installer (10.2.159.1ubuntu1) to 10.3.181.14ubuntu0.11.04.1
geoclue (0.12.0-1ubuntu8) to 0.12.0-1ubuntu8.1
gnome-nettool (2.32.0-0ubuntu1) to 2.32.0-0ubuntu1.1
im-switch (1.20ubuntu3) to 1.20ubuntu3.1
language-pack-en (1:11.04+20110421) to 1:11.04+20110509
language-pack-gnome-en (1:11.04+20110421) to 1:11.04+20110509
language-selector-common (0.34) to 0.34.2
language-selector-gnome (0.34) to 0.34.2
libgeoclue0 (0.12.0-1ubuntu8) to 0.12.0-1ubuntu8.1
libntrack-qt4-1 (011-1ubuntu1) to 011-1ubuntu1.1
libntrack0 (011-1ubuntu1) to 011-1ubuntu1.1
libtelepathy-logger2 (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
ntrack-module-libnl-0 (011-1ubuntu1) to 011-1ubuntu1.1
python-papyon (0.5.5-1ubuntu1.1) to 0.5.5-1ubuntu1.2
software-center (4.0.1) to 4.0.2
telepathy-logger (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
x11-common (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg-dev (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-common (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-core (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-dev (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-input-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-video-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1

It didn't help me out (I assume he meant to use system update on packages), but it might work for you guys.

---

### Post by murmilad on 2011-10-21
I'm not professional, but i found some poor workaround for Ubuntu 11.10:

Ubuntu has  a */sys/module/* parameter, that enables/disables Audio Powersave (Speakers Pop) you just can point '0' topba* /sys/module/snd_ac97_codec/parameters/enable_loock* and this feature will be disabled at the moment.

And it is some scripts in the pm-utils, that start/stop some features when you plug in/plug out a power cable.
Script **intel-audio-powersave** is for Audio Powersave feature

So, to turn off Audio Powersave for Intel (Speakers Pop) you can:
1) *#rm /usr/lib/pm-utils/power.d/intel-audio-powersave*
2) [I]#echo 0 > /sys/module/snd_ac97_codec/parameters/enable_loopback


[/I]

---

### Post by bendertherobit on 2011-12-13
I have a HP dv2000 and had the same problem on 11.04.  I did a clean install of 11.10 but the issue is still there. I had 9.04 installed at one time and the alsabase fix worked then, but not on 11

---

