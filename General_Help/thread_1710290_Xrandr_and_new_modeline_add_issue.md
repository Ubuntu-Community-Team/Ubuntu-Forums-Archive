---
title: "Xrandr and new modeline add issue"
date: 2011-03-19
forum: General Help
---

### Post by fight2survive on 2011-03-19
im trying to add a 1920x1080 screen resolution to my computer. i am currently using Maverick meerkat, and a GTX460 nvidia video card, on a DVI output.
i found another thread where the OP had the same problem as me, but he didn't have the same video card as me, so i'm stuck where he got helped.
[http://ubuntuforums.org/showthread.php?t=1594308](http://ubuntuforums.org/showthread.php?t=1594308)

i tried adding a modeline, i get the "failed to get size of gamma" error everytime.
please help!!

---

### Post by fight2survive on 2011-03-20
help!? :confused:

---

### Post by Dejavou42 on 2011-03-20
We need to know what graphics card you have. Please post the output  of ```
lspci |grep VGA
```.

Also, we will need to know the exact output of the xrandr command that you are running. post it back here.

We also need to know the output of ```
xrandr
```. Your system may not be capable of the resolution that you're trying to use.

You may have to manually add the mode to the config file, but that  is a last resort.

---

### Post by realzippy on 2011-03-20
Do you use the nvidia driver?
If so,the driver should get the monitor data (EDID) and provide your 1920 resolution in *nvidia-settings*.....

---

### Post by fight2survive on 2011-03-20
i got it fixed! turned out it was an issue with the screen itself (had to set it up so it would auto fit the image)...now i feel stupid!

---

### Post by realzippy on 2011-03-21
nah,not stupid,Happens from time to time....
Anyway,please mark thread as solved (threadtools).

---

