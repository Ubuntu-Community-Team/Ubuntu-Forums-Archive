---
title: "No Audio Out of Nowhere"
date: 2011-07-27
forum: General Help
---

### Post by gattz on 2011-07-27
I was watching videos with audio literally minutes ago, and all of the sudden my laptop has absolutely no sound. I have no idea what could have caused it. I just ran a quick update and restarted, didn't fix it. I also went under Preferences > Sound > Hardware and did a speaker test, no sound. What could have possibly happened? Is this a common issue? Is my integrated audio burnt out or something?

(No, I don't have mute on.)

---

### Post by 23dornot23d on 2011-07-27
Could be a hardware problem .... or have you just done a update upgrade ..... or did one run automatically
and does the headphone socket work ?

Enter these in a terminal and post what information it gives back ......

[B]aplay -l
[/B] 
[B]dpkg -l | grep "alsa"
[/B] 
[B]head -n 1 /proc/asound/card*/codec#*
[/B] 

Do any of the above commands give any info back ....... sound is not  my thing but some more information may help others to find a solution to this ......

---

### Post by SoulTechnologist on 2011-07-27
Happened to me once on a Dell XPS 1710. Try simply by restarting Ubuntu. Is Ubuntu the only OS you have on your laptop? If not, have you tested the other OS to see if problem persists?

---

### Post by gattz on 2011-07-27
> **23dornot23d said:**
> Could be a hardware problem .... or have you just done a update upgrade ..... or did one run automatically
and does the headphone socket work ?

Enter these in a terminal and post what information it gives back ......

[B]aplay -l
[/B] 
[B]dpkg -l | grep "alsa"
[/B] 
[B]head -n 1 /proc/asound/card*/codec#*
[/B] 

Do any of the above commands give any info back ....... sound is not  my thing but some more information may help others to find a solution to this ......
[B]kain@kain-Precision-M4400:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kain@kain-Precision-M4400:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                            1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                            4.69-0ubuntu2                                     Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.30-2                                         GStreamer plugin for ALSA
kain@kain-Precision-M4400:~$ head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD71B7X
[/B]
I just did a basic update with the update manager. I did it after the problem showed up though. The headphone socket does not work. I can hear static when I plug it in and unplug it though.

**@SoulTechnologist** 
I tried that but had no luck. Ubuntu is the only OS on the machine. I'm on a Dell Precision M4400 by the way.

---

### Post by gattz on 2011-07-27
Bump...

---

