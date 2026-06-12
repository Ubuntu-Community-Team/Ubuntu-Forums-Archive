---
title: "No user/availability applet in Indicator Applet Complete?"
date: 2011-09-17
forum: General Help
---

### Post by Pragu on 2011-09-17
Hello all, just a minor problem here. When I booted up this morning I noticed there was no longer the applet in my panel that had my name and my availability for Empathy. I'm not sure what it is called, nor why it is missing, nor how to get it back. Any help would be much appreciated!

11.04 Ubuntu Classic

edit: picture
[IMG]http://i.imgur.com/6ERsZ.png[/IMG]

---

### Post by Frogs Hair on 2011-09-17
Try this terminal command to restore the panel applets to default .```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```The package name for Gmome  is indicator-applet-session and  can be found in the synaptic package manager . The messenger applet is indicator-me .

---

### Post by Pragu on 2011-09-17
That did the trick. Thank you very much!

---

