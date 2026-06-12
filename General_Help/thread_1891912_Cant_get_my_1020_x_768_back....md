---
title: "Cant get my 1020 x 768 back..."
date: 2011-12-06
forum: General Help
---

### Post by blakeljb on 2011-12-06
Newbie.  First post and can't seem to find anything in the forum archives that will work.  I was trying to force it to 1600 x 1200 with some other drivers.  Went back to an xorg.conf that I thought had worked but it isn't.  

My xorg.conf follows

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24           
Modes    "1600x1200" "1024x768" "640x480"

When I put in xrandr, I get the following.
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

Suggestions on where to look next?????

---

### Post by mikewhatever on 2011-12-06
What other drivers?

---

### Post by SteveDee on 2011-12-07
> **blakeljb said:**
> ...Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480....Suggestions on where to look next?????

You don't say what version of ?buntu you are running. If its a recent version, I'd start by renaming your xorg.conf file (to say: xorg.old) as you generally do not need this file to get your system running. Its simply used for customisation since ?buntu 10.something.

Then restart. Then run xrandr again.

If it still shows 640 x 480 max then you probably do have a video driver issue.

---

### Post by blakeljb on 2011-12-07
installed startup-manager, rebooted and got it back.....

---

