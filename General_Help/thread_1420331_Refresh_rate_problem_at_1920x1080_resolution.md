---
title: "Refresh rate problem at 1920x1080 resolution"
date: 2010-03-02
forum: General Help
---

### Post by deusdies on 2010-03-02
Hello,

I just installed Ubuntu 9.10

I have ATi HD5700 and its Catalyst drivers downloaded from [http://ati.amd.com](http://ati.amd.com)

The monitor is Hanns-G HH251 (25", 1920x1080@60 max)

I cannot make either "Display Settings" or "ATI Configuration" to show the refresh rate of 60 Hz as available. When I change the resolution to 1440x900 then I can pick 60 (but obviously I don't want that resolution). However, if I pick 1920x1080, the only two refresh rates available are 25 and 30 Hz, causing the image to flicker and whatnot. 

Any suggestions?

---

### Post by darolu on 2010-03-03
Read this links:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

Then you can try something like:
```
$ xrandr --output VGA-0 --mode 1920x1080 --rate 60
```

---

### Post by deusdies on 2010-03-03
Thanks, that didn't help. Here's a weird thing that happens though. 

Note: I am currently running a 1440x900 resolution.

When I type
```
xrandr --output DFP2 --mode 1920x1080 --rate 60
```The screen refreshes (goes off and back on) and I get 1920x1080 @ 30Hz. If I type --rate 25, the screen refreshes again. But if I am at --rate 60 and then type --rate 75, or --rate 55 (anything but 25), nothing happens. The command is executed, no errors are reported, but nothing happens.

Also, I tried adding modes with xrandr and it didn't help.

One thing I did not tell you: the monitor is apparently not recognized in xorg.conf . The "Display" under Settings sees it as "HSD24", but xorg.conf says "ATI generic display" or something like that.

---

### Post by deusdies on 2010-03-03
Here's one more weird thing. This is the (beginning) of my xrandr output:

```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1440x900+0+0 (normal left inverted right x axis y axis) 543mm x 305mm
   1920x1080      30.0 +   25.0     30.0     25.0     30.0     25.0     30.0     25.0     30.0 
```

I see only 30 and 25? :/

EDIT: Just connected my monitor via VGA cable. Now it works fine. Still, I'd prefer to use HDMI if at all possible.

---

