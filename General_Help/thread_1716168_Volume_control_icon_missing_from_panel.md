---
title: "Volume control icon missing from panel"
date: 2011-03-28
forum: General Help
---

### Post by apoorvumang on 2011-03-28
I was having some problems with audio and java ([http://ubuntuforums.org/showthread.php?p=10609906#post10609906](http://ubuntuforums.org/showthread.php?p=10609906#post10609906)), so I uninstalled pulseaudio, which removed the volume control icon from the notification area. However, even after reinstalling pulseaudio and ubuntu-desktop(which got removed), the sound control isn't there, although the internet connection icon in the notification area is still there

Note: Another thread said that adding notification area to the panel would restore it. I've tried that, but it only shows the internet icon and not the volume control.

I'm a complete newbie btw, so dunno what to do.

---

### Post by Mr. ViC on 2011-03-28
Add the indicator applet to the panel.

---

### Post by apoorvumang on 2011-03-28
I tried, but the sound icon still doesn't come, only mail and dropbox.

---

### Post by prshah on 2011-03-28
> **apoorvumang said:**
> I tried, but the sound icon still doesn't come, only mail and dropbox.

Press Alt-F2, then give the command ```
gnome-volume-control-applet
``` (Note the "-applet"; without that, it will launch some other program).

If it still fails to appear, then please add the indicator applet as mentioned previously.

---

### Post by apoorvumang on 2011-03-28
That did it, although I just realized that it was happening because indicator-sound somehow got uninstalled.

---

