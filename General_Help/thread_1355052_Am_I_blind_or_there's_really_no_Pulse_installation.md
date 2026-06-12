---
title: "Am I blind or there's really no Pulse installation guides out there ?"
date: 2009-12-14
forum: General Help
---

### Post by Physical Hook on 2009-12-14
Have been trying to find one for the past 10 minutes. I used to use one from the [https://help.ubuntu.com/community](https://help.ubuntu.com/community) but now it appears to be gone.
Any suggestions ? Where can I find a tutorial on how to install Pulse ( I simply don't know the name of the packages .. there were quite few of them ) ?

---

### Post by wojox on 2009-12-14
What are you running 9.04, 8.10 ?

---

### Post by Physical Hook on 2009-12-14
Ubuntu 9.10 Minimal CD + Openbox. ALSA is already installed.

---

### Post by wojox on 2009-12-14
Ahh the old minimal CD. Well here is what

```
dpkg -l | grep pulse
``` 

Rendered

```

ii  gstreamer0.10-pulseaudio              0.10.16-1ubuntu3                                        GStreamer plugin for PulseAudio
ii  libcanberra-pulse                     0.15-0ubuntu7                                           a simple abstract interface for playing even
ii  libpulse-browse0                      1:0.9.19-0ubuntu4                                       PulseAudio client libraries (zeroconf suppor
ii  libpulse-mainloop-glib0               1:0.9.19-0ubuntu4                                       PulseAudio client libraries (glib support)
ii  libpulse0                             1:0.9.19-0ubuntu4                                       PulseAudio client libraries
ii  pulseaudio                            1:0.9.19-0ubuntu4                                       PulseAudio sound server
ii  pulseaudio-esound-compat              1:0.9.19-0ubuntu4                                       PulseAudio ESD compatibility layer
ii  pulseaudio-module-bluetooth           1:0.9.19-0ubuntu4                                       Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-gconf               1:0.9.19-0ubuntu4                                       GConf module for PulseAudio sound server
ii  pulseaudio-module-udev                1:0.9.19-0ubuntu4                                       udev device detection module for PulseAudio 
ii  pulseaudio-module-x11                 1:0.9.19-0ubuntu4                                       X11 module for PulseAudio sound server
ii  pulseaudio-utils                      1:0.9.19-0ubuntu4                                       Command line tools for the PulseAudio sound 

```

That may get you started on the right track.

---

### Post by Physical Hook on 2009-12-15
Thank you. Everything is working now :)

---

### Post by wojox on 2009-12-15
Just in case:

```
sudo apt-get install pulseaudio pavucontrol padevchooser
```

---

