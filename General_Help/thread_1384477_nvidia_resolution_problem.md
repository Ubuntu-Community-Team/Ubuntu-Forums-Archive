---
title: "nvidia resolution problem"
date: 2010-01-18
forum: General Help
---

### Post by leehach on 2010-01-18
Just installed a GeForce 7200 GS and I'm having a resolution problem with the proprietary nvidia drivers. I'll describe the problem first, then how I tried to solve it.

**The Problem:** The display has some kind of phase effect as if the display resolution doesn't match what the monitor is capable of. For graphical stuff the effect is minor enough as to not be noticed. However, it has the effect of making text slightly fuzzy and the size of individual characters varies. It is most noticeable if you type a string of the same letter in a text editor. From the left to the right of the window the letter gets slightly skinnier, then slightly fatter, then slightly skinnier, … 

**Attempted Solutions**

1. My monitor has a 5:4 aspect ratio. Most standard resolutions (1024x768, 1152x864, etc.) are 4:3. I created a 5:4 resolution of 1080x864 and added it to xorg.conf with
```
ModeLine       "1080x864@60" 76.00 1080 1136 1248 1416 864 867 874 897 -hsync +vsync
```
This added a 1080x864 resolution which I can choose with the NVIDIA X Server Settings applet, but it did not fix the problem.

2. Several how-tos describe font problem with nvidia and how to change the DPI settings in xorg.conf. 
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    Option         "UseEdidDpi" "false"
    Option         "Dpi" "81 x 81"
EndSection

```(For example, see [http://my.opera.com/CrazyTerabyte/blog/2006/02/20/nvidia-vs-fonts]("http://my.opera.com/CrazyTerabyte/blog/2006/02/20/nvidia-vs-fonts").) I think the correct DPI is 81, but neither that nor several other settings between 75 and 120 fixed the problem.

At this point I'm not convinced that it's a font problem per se, I think it's just most noticeable with fonts. This problem does not happen with the community driver (nv) or with the vesa driver.

So first, any possible solutions? Second, if you don't know of a solution, can you think of how to Google for one? Googling "ubuntu nvidia front problem" led me in the wrong direction.

PS: Also might try to test out a different monitor with different aspect ratio and native resolutions but it will take me a couple of days to get my hands on one. In the meantime, any help will be appreciated.

---

### Post by DestructionsRightHand on 2010-01-18
did you enable extra visual effects?  I believe this turns on graphics acceleration and font smothing.  If it does not you can enable them manually

---

### Post by leehach on 2010-01-18
If you mean Compiz, yes, but the font issue persists. Yes, to font smoothing as well.

---

### Post by leehach on 2010-01-21
OK, a lot of help here: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/1203126.html]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/1203126.html")

First, created an image file with one black pixel and one white pixel. Set my desktop to use that tile that image. The 1080x864 custom resolution and the 1152x864 standard resolution showed banding indicating that this was not merely a font problem. I found that other resolutions worked without banding, including 1024x768 (not enough screen real estate) and 1280x960. So now I'm running at 1280x960 and everything looks great. Still doesn't explain why 1152x864 produces banding, but I'll just avoid that resolution.

---

