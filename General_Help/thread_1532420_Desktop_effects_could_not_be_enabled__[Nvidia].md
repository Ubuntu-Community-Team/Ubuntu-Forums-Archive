---
title: "Desktop effects could not be enabled  [Nvidia]"
date: 2010-07-16
forum: General Help
---

### Post by usersock on 2010-07-16
This all started when I installed Gnome Do, and it required me to enable compositing, so I enabled "Extra" in Visual Effects. I didn't like some of the effects so I installed Simple CompizConfig Settings Manager. A few hours later I uninstalled Gnome Do, and installed Cairo Dock. I noticed my Visual Effects had reset to "None", and when selecting any other option, I get the error: **Desktop effects could not be enabled.**

After a bit of research I found I should check a few things. Here are their results: 


**When opening the Nvidia controls under System/Admin/Nvidia X Server Settings**:
```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```[B]

After running nvidia-xconfig in terminal: [/B]
```
Using X configuration file: "/etc/X11/xorg.conf"

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```[B]

Typing compiz in terminal:[/B]
```
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
```

---

### Post by dino99 on 2010-07-16
actual kernel directly deals with X, so remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

nvidia-current need to be activated: system admin hardware driver

---

### Post by usersock on 2010-07-16
I entered "sudo rm -f /etc/X11/xorg.conf" into the terminal and then made sure the correct driver was selected (it was). After a reboot, the problem persists :(

---

