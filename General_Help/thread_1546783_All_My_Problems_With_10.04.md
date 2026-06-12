---
title: "All My Problems With 10.04"
date: 2010-08-05
forum: General Help
---

### Post by What Rights on 2010-08-05
[LIST=1]
[*]Mouse Lag
[*]Sound Glitches
[*]Slow and Torn Video
[/LIST]

Ok, well as for the mouse lag, The mouse only lags sometimes, and I do not know whether it is because of HDD activity or not, but I do not think it makes a difference.

ALSA/Pulseaudio has caused me some glitches or stops and starts while playing audio, and I know my sound card is fine because everything worked fine in windows.

As for my slow and torn video, I have just been able to fix the tearing in gnome, but the problem still persists to video V sync is activated for Open GL and X configuration.


Thanks to all who can help.

---

### Post by tekkidd on 2010-08-05
Try an update or a format reinstall

---

### Post by What Rights on 2010-08-05
> **tekkidd said:**
> Try an update or a format reinstall


Thanks for the help, But I just reinstalled yesterday, and yeah that is format reinstall.

---

### Post by Jesus_Valdez on 2010-08-05
maybe plating with compiz, turn on and off and see if there's a difference.

---

### Post by What Rights on 2010-08-05
> **Jesus_Valdez said:**
> maybe plating with compiz, turn on and off and see if there's a difference.


See that is the thing, I need compiz so my video doesn't tear (as much) and so windows don't tear.

---

### Post by lidex on 2010-08-06
For your audio you may want to see this:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html](http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html)
Meanwhile can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by What Rights on 2010-08-06
HP G60 121WM

```
Linux conner-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
``````
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA

``````
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20561 (Hermosa)

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP78 HDMI

```

---

### Post by What Rights on 2010-08-06
Bump for help today.

---

### Post by lidex on 2010-08-06
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. On the output tab choose the correct device.

---

### Post by What Rights on 2010-08-06
I did all of that, It seems fine, thanks for your help.

---

### Post by lidex on 2010-08-06
Nice. Keep your fingers crossed.

---

