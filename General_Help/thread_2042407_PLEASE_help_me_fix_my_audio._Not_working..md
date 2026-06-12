---
title: "PLEASE help me fix my audio. Not working."
date: 2012-08-14
forum: General Help
---

### Post by janderson91z on 2012-08-14
I have an old Compaq Presario SR1603WM that I'd like to use as a second computer and revive with Lubuntu 12.04. I've tried turning up the volume of everything in alsamixer but it just doesn't work. Please help. Thank you.

---

### Post by Alvaro_SG on 2012-08-14
Try with this:

```
sudo apt-get install alsa-lib alsa-utils gstreamer0.10-base-plugins gstreamer0.10-good-plugins gstreamer0.10-bad-plugins gstreamer0.10-ugly-plugins
```

---

### Post by janderson91z on 2012-08-14
I got this error.

```
E: Unable to locate package alsa-lib
E: Unable to locate package gstreamer0.10-base-plugins
E: Couldn't find any package by regex 'gstreamer0.10-base-plugins'
E: Unable to locate package gstreamer0.10-good-plugins
E: Couldn't find any package by regex 'gstreamer0.10-good-plugins'
E: Unable to locate package gstreamer0.10-bad-plugins
E: Couldn't find any package by regex 'gstreamer0.10-bad-plugins'
E: Unable to locate package gstreamer0.10-ugly-plugins
E: Couldn't find any package by regex 'gstreamer0.10-ugly-plugins'

```

---

