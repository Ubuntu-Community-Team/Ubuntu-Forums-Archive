---
title: "ECS GF8200A Sound"
date: 2009-11-13
forum: General Help
---

### Post by Sezotove on 2009-11-13
Well when it comes to linux im not the smartest.  Alright for about the last 24 hours i have been looking and doing everything i can find to get my mic to work. I have jumped from using Pulse Audio or Esound(i think thats it) to everything else.  I can play Audio no problem, but my mic has horrific static in it, and theres no end to it. Anytime i use Pulse everything get royally dominated.  

This giude
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

dominated all sound what so ever.


with aplay -L i get 

```
sezotove@sezotove-desktop:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

in my sound prefs i have this

[IMG]http://img.photobucket.com/albums/v243/sezotove/soundpref.png[/IMG]

I really dont know what else to do. I know the mic works, i know it is supposed to have a sound boost, and i know this  because it was working fine in Windows, but then again windows craped out on me so... 

Thanks in advanced.

***EDIT***
Before i had static and I ran ```
sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extra

```

and now i have no static on the mic but it still doesnt work im getting error msgs in Sound prefs when i try and test "Sound Capture" they are "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused"

---

