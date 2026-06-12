---
title: "Karmic 9.1 startup wallpaper but no login or GUI"
date: 2009-11-19
forum: General Help
---

### Post by horqua on 2009-11-19
I've been fighting with a new install of 9.1 and this has not been a fun experience. I should have stayed with 9.0 and not messed with the 9.1 upgrade. The install was successful but the video driver update for Nvidia totally hosed the GUI. With a normal boot, I would get the flickering screen. With the Rescue boot, I could get to the login screen and work from the command line. I finally partially solved that today by uninstalling and reinstalling a fresh xorg and blowing out the Nvidia packages. This has brought me back to the point where, when I boot and choose the normal 9.10 kernel 2.6.31-14-generic, i begin to see the initial graphical screens (wallpaper) containing the logo and ubuntu text. Then, I get the standard ubuntu wallpaper (it looks like a theatre stage with a single spotlight shining from overhead illuminating the center stage) along with a cursor. That's it. No login block, no ability to access any other features, no text, just wallpaper and a cursor. If I CTRL+F1 I can get the command line login.  CTRL+F7 gets me back to the same screen with cursor. I've tried stopping, restarting, and reinstalling the gdm. I've used the apt-get ubuntu-desktop and the aptitude-install ubuntu-desktop. Nothing seems to work. 

Can anyone help me get back to a standard, vanilla flavored GUI desktop where I can run Firefox and do all the things I've come to know and love in Ubuntu? 
Many thanks!

---

