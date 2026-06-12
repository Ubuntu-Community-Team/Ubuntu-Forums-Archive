---
title: "argh! Input Out Of Range!"
date: 2006-05-15
forum: General Help
---

### Post by Cephyr on 2006-05-15
Setting up a computer for a friend, and everything worked fine until it tried to fire up X at the end of setup. Apparently, the monitor doesn't like the signal it's getting.

"Input Signal Out Of Range" is the error message I'm getting on the monitor.

I Ctrl-Alt-F1'd to check out the terminal output, and there's no error messages (prefixed with [EE]). I did a dpkg-reconfigure on the xserver-xorg package to no avail.

FYI, the monitor is a 15" LCD flatscreen IBM T56A, and the graphics card is an Nvidia Vanta (TNT2 chipset)

---

### Post by robglinka on 2006-05-15
This isn't uncommon, basically the default screen resolutions won't work on your friend's monitor. You can fix this a couple of ways:

1- install the nvidia graphics drivers and see if that helps. (look for sudo apt-get nvidia-glx in this forum, you'll find plenty of how-to's)

2- See if you can run the screen at a smaller resolution, the default is 1024x768.

To try option two, you need to edit the xorg.conf file in the /etc/X11/ folder.

---

### Post by robglinka on 2006-05-15
Sorry, double post.

---

### Post by empthollow on 2006-05-15
i've run into this problem as well, in my case it not a problem with the resolution, it was a problem with the HorizSync and VertRefresh rates in my /etc/X11/xorg.conf. i added this in the monitor section to fix it:

horizsync    30.0 -50.
vertrefresh  45.0 - 60.0

hope this helps

---

