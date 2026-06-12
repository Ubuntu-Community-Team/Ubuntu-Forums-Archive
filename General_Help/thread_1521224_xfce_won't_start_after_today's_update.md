---
title: "xfce won't start after today's update"
date: 2010-06-30
forum: General Help
---

### Post by sparty_xubunter on 2010-06-30
Did anyone else have this happen? 

I've been using 10.04 with all the appropriate Nvidia drivers and stuff for a substantial time now.  Did the synaptic update this morning, it told me to reboot, I did, and now all I get is the terminal after boot.  Asked for xfce/xterm and it said display not found.

When going to Grub and booting from the .22 kernell xfce starts and works fine though.

Tried searching but didn't see anyone else with this problem.

Thoughts?  I'm not a linux expert, just someone who learns while using xubuntu for the past 2 years.

---

### Post by Blodskaal on 2010-06-30
I'm a noob to linux, and I'm using Ubuntu instead of Xubuntu, but I had something similar on Ubuntu after today's update, the problems might be related.

I use a non-distro nVidia driver. The Xorg update alway overwrites a symbolic link, placed by the nVidia install, with a file. So if you run a non-distro nVidia driver on Ubuntu, you'll have to reinstall your driver after every Xorg update or your GLX won't work.

<<This isn't much of a problem since Xorg updates don't happen that often. I've been using Ubuntu for three months now, and this was the first time I encountered the problem.>>

Maybe in Xubuntu something similar happens, and you've got to reinstall your nVidia driver.

---

### Post by sparty_xubunter on 2010-06-30
I think you're right - sort of.  I didn't have to reinstall the driver, but after resetting the xorg driver to vesa I was able to get it to restart and then set it back to Nvidea and then it worked.  I'm guessing this was not the right way to do it however.

---

