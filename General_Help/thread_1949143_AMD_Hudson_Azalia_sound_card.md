---
title: "AMD Hudson Azalia sound card"
date: 2012-03-29
forum: General Help
---

### Post by mike555 on 2012-03-29
A friend of mine has a AMD Hudson Azalia sound card and can't seem to get any sound out of it , any suggestions, or isn't it supported.

---

### Post by idoitprone on 2012-03-29
> **mike555 said:**
> A friend of mine has a AMD Hudson Azalia sound card and can't seem to get any sound out of it , any suggestions, or isn't it supported.


well it might help if you give us the details of your card

```
lspci -vnn | grep -iA5 audio
``````
aplay -l
``````

pactl list
pactl info

```while your at it
your alsa version

```
dpkg -l | grep alsa
```

---

### Post by TheBig3 on 2012-06-20
Having the same problem on a Samsung Notebook model NP305E5A-A01US. Here is my info:
```
thebig3@ubuntu:~$ lspci -vnn | grep -iA5 audio
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
	Subsystem: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
--
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c624]
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
```


```
thebig3@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
thebig3@ubuntu:~$ pactl list
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

thebig3@ubuntu:~$ pactl info
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```


```
thebig3@ubuntu:~$ dpkg -l | grep alsa
ii  alsa-base                            1.0.25+dfsg-0ubuntu1                    ALSA driver configuration files
ii  alsa-utils                           1.0.25-1ubuntu5                         Utilities for configuring and using ALSA
ii  alsamixergui                         0.9.0rc2-1-9.1                          graphical soundcard mixer for ALSA soundcard driver

```

Haven't tried hooking up the hdmi yet to see if the audio works that way. I am currently using Lubuntu 12.04. Any help is much appreciated, thank you.

---

### Post by TheBig3 on 2012-06-20
Just got it working....

Went in to synaptic and used search for "pulse audio" and installed a bunch of stuff... Here is a list of what I installed, don't know which one worked though.

```
Installed the following packages:
avahi-daemon (0.6.30-5ubuntu2)
csladspa (1:5.17.6~dfsg-1ubuntu0.1)
csound (1:5.17.6~dfsg-1ubuntu0.1)
csound-data (1:5.17.6~dfsg-1ubuntu0.1)
csound-gui (1:5.17.6~dfsg-1ubuntu0.1)
csound-manpages (1:5.13~dfsg-1)
csound-utils (1:5.17.6~dfsg-1ubuntu0.1)
dnet-common (2.58ubuntu1)
gstreamer0.10-pulseaudio (0.10.31-1ubuntu1)
guile-2.0 (2.0.5+1-1)
guile-2.0-libs (2.0.5+1-1)
libao-common (1.1.0-1ubuntu2)
libao4 (1.1.0-1ubuntu2)
libavahi-core7 (0.6.30-5ubuntu2)
libcelt0-0 (0.7.1-1)
libcsound64-5.2 (1:5.17.6~dfsg-1ubuntu0.1)
libdaemon0 (0.14-2)
libdnet (2.58ubuntu1)
libfftw3-3 (3.3-1ubuntu1)
libgc1c2 (1:7.1-8build1)
libgconfmm-2.6-1c2 (2.28.0-1)
libglademm-2.4-1c2a (2.6.7-2build1)
libgsl0ldbl (1.15+dfsg-1build1)
libgtkmm-2.4-1c2a (1:2.24.2-1ubuntu1)
libnss-mdns (0.10-3.2)
libroar-compat1 (0.4-2)
libroar1 (0.4-2)
librtaudio4 (4.0.10~ds0-2)
librtmidi1 (1.0.15~ds0-2)
libstk0c2a (4.4.3-2)
paman (0.9.4-1ubuntu3)
paprefs (0.9.10-0ubuntu1)
pavumeter (0.9.3-1ubuntu2)
pulseaudio (1:1.1-0ubuntu15.1)
pulseaudio-esound-compat (1:1.1-0ubuntu15.1)
pulseaudio-module-gconf (1:1.1-0ubuntu15.1)
pulseaudio-module-x11 (1:1.1-0ubuntu15.1)
pulseaudio-module-zeroconf (1:1.1-0ubuntu15.1)
rtkit (0.10-2)
snd (11.7-1ubuntu1)
snd-gtk-pulse (11.7-1ubuntu1)
stk (4.4.3-2)
tcl8.4 (8.4.19-4ubuntu3)
tk8.4 (8.4.19-4)
xmms2-core (0.8+dfsg-2)
xmms2-plugin-pulse (0.8+dfsg-2)
```

Glad I got it working, just wish I knew how....:-k  :-?

---

### Post by idoitprone on 2012-06-20
> **TheBig3 said:**
> ```
thebig3@ubuntu:~$ pactl list
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

thebig3@ubuntu:~$ pactl info
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```

i think pulse audio is not configured with the proper dependencies

---

