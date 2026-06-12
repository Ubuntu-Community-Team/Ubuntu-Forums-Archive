---
title: "Making gif files using Gimp"
date: 2011-03-24
forum: General Help
---

### Post by TimEnid on 2011-03-24
ok, so im following these directions
```
mplayer -ao null -loop 0 -ss 0:0:33 -endpos 2 medianame.avi
mplayer -ao null -ss 0:6:26 -endpos 3 medianame.avi -vo jpeg:outdir=animated_gifcd 
```

when i put in a movie that say has one name like "christmas.avi" it works fine, but if i put in a name like "dead space aftermath.avi" i get error messages saying that it can find "dead", cant find "space" and cant find "aftermath". any idea how to fix this? I made sure to type everything correctly.

---

### Post by flipper T on 2011-03-24
rename the avi & leaving out the spaces ?

---

### Post by WorMzy on 2011-03-24
Put quote marks around the name.
e.g.
```
mplayer -ao null -loop 0 -ss 0:0:33 -endpos 2 "media name.avi"
```

---

### Post by TimEnid on 2011-03-24
> **WorMzy said:**
> Put quote marks around the name.
e.g.
```
mplayer -ao null -loop 0 -ss 0:0:33 -endpos 2 "media name.avi"
```

this worked. thanks a lot.

---

### Post by TimEnid on 2011-03-24
ok, so when i do certain parts of this movie, it works fine. but if i go to a different time frame, i get the following
```
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  512x384  12bpp  29.970 fps  1088.6 kbps (132.9 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
```

---

### Post by SeijiSensei on 2011-03-24
Somewhere, maybe in ~/.mplayer/config, you've told mplayer to use the VDPAU output device.  That only works with recent NVIDIA cards and then only using the proprietary driver.  Since your signature reports that you have a Radeon adapter, you can't use VDPAU.

Try using the xv driver instead.  For a test, add the option "-vo xv" to your mplayer command.  Does that fix the problem?  If so, you need to track down where you specified VDPAU as your video driver.

If you install smplayer, you can easily switch among the available drivers by going to Options > Preferences > General and clicking the Video tab at the top.

---

