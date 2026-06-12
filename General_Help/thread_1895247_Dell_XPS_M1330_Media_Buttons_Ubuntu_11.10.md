---
title: "Dell XPS M1330 Media Buttons Ubuntu 11.10"
date: 2011-12-14
forum: General Help
---

### Post by x C0MMAND0 x on 2011-12-14
The media buttons (mute, volume up, volume down etc) are not working.  If I look at keyboard shortcuts and reset the buttons, my system detects when I press them, but for some reason it doesn't actually change the volume or mute it or anything.

Any ideas?

---

### Post by x C0MMAND0 x on 2011-12-14
I solved it. 

Fix: 
```
sudo apt-get install kmix
```

Then remove gnome-sound-applet from startup applications,

Add kmix to the startup applications

Manually run kmix and go into the configuration options and set it to dock to system tray.

Fixed!

---

