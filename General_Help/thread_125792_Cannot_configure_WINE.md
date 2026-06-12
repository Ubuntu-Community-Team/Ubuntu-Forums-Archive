---
title: "Cannot configure WINE"
date: 2006-02-04
forum: General Help
---

### Post by plexi50 on 2006-02-04
Installed WINE from Synaptic Ok, but when I run winecfg, it generates the following error and will not run:

Xlib:  extension "GLX" missing on display ":0.0".

followed by a long screen before it shuts down. Seems like some kind of video issue, but everything else is ok. Ideas?

---

### Post by dcstar on 2006-02-04
[QUOTE=plexi50]Installed WINE from Synaptic Ok, but when I run winecfg, it generates the following error and will not run:

Xlib:  extension "GLX" missing on display ":0.0".

followed by a long screen before it shuts down. Seems like some kind of video issue, but everything else is ok. Ideas?[/QUOTE]
Rename you hidden .wine folder to something else, and try winecfg again.

If it still happens, it may be an issue with your video hardware driver.

You may also want to add this to your /etc/apt/sources.list file to get the latest Wine:

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/

---

### Post by plexi50 on 2006-02-05
Solved---problem was the Nvidia Glx driver. I purged the driver and wine installed and runs fine. I will try to reinstall the driver later to see if it makes any diff, I really don't need it, the default is fine for me.

---

