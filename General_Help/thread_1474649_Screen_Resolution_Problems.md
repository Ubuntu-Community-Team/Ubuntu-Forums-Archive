---
title: "Screen Resolution Problems"
date: 2010-05-06
forum: General Help
---

### Post by wabbit46 on 2010-05-06
I have recently upgraded to Ubuntu 10.04 and installed the nVidia video driver for my computer. Everything was working perfectly.

Today when I started the computer none of the menus were visible.
It seems like the screen resolution has changed and the menu's are beyond the visible area. All I can see is the wallpaper.

I know it is functioning correctly as I can see the SAMBA shares on my Windows computer.

Does anyone have any idea how I can reset the video and make the computer usable again ?

---

### Post by junapp on 2010-05-06
out of curiosity:
ALT-F2
type 'gnome-terminal'
then type 'sudo killall gnome-panel'
then type in your password. I've had to do this to clean up my notification area a number of times, and suspect something may be whacky with the gnome-panels.

---

### Post by wabbit46 on 2010-05-07
> **junapp said:**
> out of curiosity:
ALT-F2
type 'gnome-terminal'
then type 'sudo killall gnome-panel'
then type in your password. I've had to do this to clean up my notification area a number of times, and suspect something may be whacky with the gnome-panels.

Thanks very much - it fixed it.

---

