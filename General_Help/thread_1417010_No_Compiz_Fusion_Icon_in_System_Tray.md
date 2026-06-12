---
title: "No Compiz Fusion Icon in System Tray"
date: 2010-02-26
forum: General Help
---

### Post by fishkid257936 on 2010-02-26
Ever sense I installed the KDE SC 4.4 Packages, there is no compiz fusion icon in the system tray. I tried removing the fusion-icon package and it still does not work. Am I doing something wrong?

---

### Post by Pollox on 2010-02-27
The icon is provided by the fusion-icon package, so keep that installed.  Then, make sure the program "fusion-icon" is actually running using your System Monitor.  If it isn't, add it to the list of startup programs so it will start when you log in.

---

### Post by n0dix on 2010-02-27
If you run in console compiz-icon, what happen, any error, or something?

---

### Post by fishkid257936 on 2010-02-27
This is what happens when I type fusion-icon in the terminal:
```
 * Detected Session: kde
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp
compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Close event.
```
Does the Error lots and lots of times, and yes it is showing in the system monitor.

---

### Post by n0dix on 2010-02-27
also note that kde has it's own compositing engine built in. it's quite similar to compiz. Just go to System Settings > Desktop > Desktop Effects and enable it.

---

### Post by fishkid257936 on 2010-02-27
Turning on KDE desktop effects showed me that there was a hidden panel behind the main one. I delete the main panel, and it has lots of programs in the system tray. I run fusion-icon and it shows up! :D Thanks for all your help!

---

### Post by bcollignon on 2011-06-03
* Detected Session: gnome
 * Searching for installed applications...
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.7/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.7/dist-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.7/dist-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decor'].Screen['command']
KeyError: 'decor'


Any help greatly appreciated!

---

