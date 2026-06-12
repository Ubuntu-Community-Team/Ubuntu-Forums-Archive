---
title: "no sound on laptop"
date: 2010-07-06
forum: General Help
---

### Post by jewfromdahood on 2010-07-06
I use ubuntu 10.10 and for some reason the sound doesn't work. tried everything reinstalling ALSA and alsa driver doesn't even work any help, it's a toshiba satellite L505-S6946

---

### Post by aust77 on 2010-07-06
You use Ubuntu 10.10? The development release? If so, maybe the Ubuntu developers haven't configured sound for your hardware just yet. Try the latest stable release, 10.04 it should work fine.

Cheers,


aust77

---

### Post by jewfromdahood on 2010-07-06
oh my bad 10.04

---

### Post by lidex on 2010-07-07
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

I'm assuming you made sure your sound is not muted.
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

---

### Post by jewfromdahood on 2010-07-07
tara@tara-laptop:~$ uname -a
Linux tara-laptop 2.6.35-6-generic #9-Ubuntu SMP Thu Jul 1 03:01:23 UTC 2010 x86_64 GNU/Linux
tara@tara-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tara@tara-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                          1.0.23+dfsg-1ubuntu2                            ALSA driver configuration files
ii  alsa-source                                        1.0.23+dfsg-1ubuntu2                            ALSA driver sources
ii  alsa-tools                                         1.0.23-3ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                                     1.0.23-3ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                         1.0.23-0ubuntu1                                 Utilities for configuring and using ALSA
ii  bluez-alsa                                         4.64-0ubuntu1                                   Bluetooth audio support
ii  gstreamer0.10-alsa                                 0.10.29.3-1                                     GStreamer plugin for ALSA
rc  libsdl1.2debian-alsa                               1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 

tara@tara-laptop:~$ head -n 1 /proc/asound/card0/codec#0
Codec: Realtek ALC272

tara@tara-laptop:~$ head -n 1 /proc/asound/card0/codec#1
Codec: LSI ID 1040

---

### Post by lidex on 2010-07-07
> Linux tara-laptop 2.6.35-6-generic #9-Ubuntu SMP Thu Jul 1 03:01:23 UTC 2010 x86_64 GNU/Linux

> oh my bad 10.04 

So you're using a maverick kernel on lucid? Are you pulling my leg? You should be posting in the development forum. At any rate, try this:
[http://ubuntuforums.org/showpost.php?p=9220081&postcount=8]("http://ubuntuforums.org/showpost.php?p=9220081&postcount=8")

---

