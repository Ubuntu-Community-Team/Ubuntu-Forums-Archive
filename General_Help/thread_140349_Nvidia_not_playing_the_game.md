---
title: "Nvidia not playing the game"
date: 2006-03-06
forum: General Help
---

### Post by thessem on 2006-03-06
Every single time I start up ubuntu, I have to re-install the NVIDIA drivers, or no X related things will start (I sort of need those). The NVIDIA drivers work perfectly when they are re-installed, but on rebooting the computer, the X server wont start until I put them In again.

At the moment I have just changed to a version of Xorg.conf that doesn't load the drivers, but I would like to find a way I can fix this so I can use the drivers

---

### Post by Sutekh on 2006-03-06
How did you install the drivers?

You could give this guide a shot

[Ubuntu Forums - HOWTO: Latest NVIDIA Drivers](http://ubuntuforums.org/showthread.php?t=75074)

Follow Method 1 (dead easy) to install the NVIDIA drivers in the Ubuntu repositories

Follow Method 2 (slightly harder) to install the latest NVIDIA drivers from their site

---

### Post by s|k on 2006-03-06
I had the same problem thessem, I solved it by following Method 2 in the instructions linked to above and by selecting 'no' when the installer asked me to run a xorg config utility. I had been following method two and having the same issues, but selecting no on that option and X-server started as normal after the reboot.

Try it and let us know.

Good luck.

---

### Post by soonindallas on 2006-03-06
borrow (do not buy!) an ati card and try for days on end to get 3D acceleration working.

then you'll see what video driver hell really is.

then switch back to nvidia with relief.

---

### Post by thessem on 2006-03-09
Thanks, I'll try all of the above.

and soonindallas, thats the reason why I bought nividia, and plan to stay there

---

