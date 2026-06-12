---
title: "Alternative panel volume control"
date: 2010-05-28
forum: General Help
---

### Post by jdege on 2010-05-28
The only volume control panel object I've been able to find in Ubuntu 10.04 is the Indicator Applet, and that has a bug that makes accessing the system through a remote VNC Viewer unusable.  (Every time you hit the 'M' key, it activates the applet menu.  You cannot type 'm' into a document or form without shutting off the applet.)

So, since I use VNC to remotely access the machine fairly regularly, it's either remove the applet every time I do, and add it back again when I'm running local, run without a volume control, or find another panel applet that provides for volume control. (At least until the bug-fixed version of the applet is available.)

The thing is I've not been able to find another volume control applet.  Can anyone tell me where to find one?

---

### Post by inso_741 on 2010-05-28
install awn it has its own volume control applet

---

### Post by jdege on 2010-05-28
> **inso_741 said:**
> install awn it has its own volume control applet
I'm not looking to replace the Gnome panel, or to add a second panel.  (My desktop gets cluttered enough, thanks).  I just want a button on the current panel that pops up a volume control.

---

### Post by germanix on 2010-05-28
Remove the applet as you yourself suggested then:
go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

This will give you the Gnome Volume control that looks somewhat different. Hope this helps.

---

### Post by jdege on 2010-05-28
> **germanix said:**
> Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control
That looks like it will work, thanks.

---

