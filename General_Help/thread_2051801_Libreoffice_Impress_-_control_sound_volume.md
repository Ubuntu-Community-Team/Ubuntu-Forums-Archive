---
title: "Libreoffice Impress - control sound volume?"
date: 2012-09-02
forum: General Help
---

### Post by MoebusNet on 2012-09-02
I recently got some Power Point slide shows (pps files) that combine picture slides with background music. They open full-screen and play; I can advance the slides and hear the music.

I know these files weren't designed for Libreoffice Impress, but I haven't figured out how to reduce the sound volume. No matter where my volume control is set, the pps plays at maximum volume. I can reduce system volume or even mute system volume with no effect. I haven't been able to access application volume in the upper taskbar because the pps opens at full-screen and hides the upper taskbar.

Any recommendations? Googlubuntu, Google & Forum Search have not been a friend on this one; neither has the Libreoffice Impress user's manual.

---

### Post by MoebusNet on 2012-09-03
After some meore digging, this may be related to:

[https://bugs.freedesktop.org/show_bug.cgi?id=32664](https://bugs.freedesktop.org/show_bug.cgi?id=32664)

If I understand the bug correctly, this covers not only Windows but all versions of Libreoffice.

I'll leave this open for now.

EDIT: This doesn't seem to be related to the bug I mentioned; I found a workaround.

1) Log out of Unity, log into Ubuntu Classic

2) Open the pps file or Libreoffice Impress file

3) Right-click the gnome-sound-applet (I think of it as the volume control) in the upper-right of the upper task bar and left-click Sound Preferences in the drop-down menu.

4) Left-click the Applications tab then adjust the volume in Libreoffice Impress as required.

Note: I found that gnome-sound-applet was not installed in Ubuntu Classic; I had to add it to the taskbar as outlined here:

[http://ubuntugenius.wordpress.com/2012/05/10/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-12-04-gnome-3-classicfallback/](http://ubuntugenius.wordpress.com/2012/05/10/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-12-04-gnome-3-classicfallback/)

I could not make this work in Unity because the pps file opened in full-screen with no way to change it to a window-view so I could get to the volume control.

---

