---
title: "Chrome browser scrollbar contrast"
date: 2012-05-19
forum: General Help
---

### Post by vasa1 on 2012-05-19
Any idea what controls the contrast between the thumb and the background in the Chrome browser (version 19, stable)? I'm on Xfce 4.10 on top of Ubuntu 12.04. I installed Gnome Color Chooser and used it to successfully enhance contrast in the scrollbars of things like Firefox, Seamonkey and LibreOffice. But Chrome is unaffected. (I have chosen "GTK+ theme" in Wrench, Settings.) I also logged out and logged in just in case.

---

### Post by vasa1 on 2012-05-19
I'm attaching a screenie that illustrates the problem enclosed in the red ellipse.

---

### Post by vasa1 on 2012-06-17
There seems to be an extant bug:
Ayatana Design >> Bugs >> [URL="https://bugs.launchpad.net/ayatana-design/+bug/721786"]Bug #721786
[/URL](Non-overlay) scroll-bar lacks sufficient contrast to easily identify its position in the scroll-track

---

### Post by vasa1 on 2012-08-05
Comment #11 in the bug mentioned above fixes my problem with the Chrome scrollbar contrast when using the Ambiance theme.
Reducing the value in line #26 darkens the trough thereby inproving contrast.
The same fix should be applicable for Radiance or themes that have a chromium.rc file.

---

