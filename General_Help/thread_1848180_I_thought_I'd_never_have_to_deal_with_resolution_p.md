---
title: "I thought I'd never have to deal with resolution problems again!"
date: 2011-09-22
forum: General Help
---

### Post by StephanG on 2011-09-22
I just installed Lubuntu onto an old laptop to breathe new life into it.  It's a 2.6 GHz (Single Core) Mecer laptop with 504 MB memory.

As I hoped it runs beautifully fast.  The resolution "density" (sorry can't think what else to call it) seems to be running fine, but it's only using a tiny portion of the screen.  The desktop seems to be forced to a size of 640x480 and only uses the top, left part of the screen.

In "Monitor Settings" it refuses to let me set my resolution any higher than 640x480.

Thanks in advance for your help.

---

### Post by dino99 on 2011-09-22
first, check the graphic driver activation (which one is used ?)

if you have an xorg.conf, try without it as actual kernel directly deal with X (some CRT/TV need it mostly for refresh rates)

sudo rm /etc/X11/xorg.conf

---

### Post by StephanG on 2011-09-22
Just a quick update, I tried a few things with XRandR and a script.  Both tell me that they "Failed to get size of gamma for output default"

And there are no other outputs besides "default"

---

### Post by whatthefunk on 2011-09-22
What resolution do you want?

---

### Post by StephanG on 2011-09-22
I don't have a Xorg.conf file.  And the "Additional Drivers" app, tells me that there are no drivers available for this machine.  It looks like an old, onboard Intel Graphics card that it's using.

The screen has a native resolution of 1280x1024.

Also:  I just plugged a VGA monitor into the laptop, and although nothing showed on the external screen, the laptop's monitor showed the correct resolution when I rebooted.  But when I unplugged the monitor, the laptop was back to using only a tiny portion of its screen.

---

### Post by whatthefunk on 2011-09-22
First, lets try to generate an Xorg file.
```
sudo Xorg --configure
```

This should generate an Xorg file and put it in your home directory.  Open up a terminal or file manager to find it.  Copy this file to /etc/X11  Restart and see if you can change the resolution now.

Didn't work?  Lets try to add a new resolution.

Open a terminal and type:
```
cvg 1280 1024
```

You should get something that looks like this:
```
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline **"1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync**
```

We're interested in the second line, the info that I put in bold.  In the terminal type:
```
xrandr --newmode **info in bold above***
```

So youre full command should look something like this:
```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

Next, we need to find out what your system calls your monitor.  It seems like it calls it "default" but lets just make sure.
```
xrandr -q
```

Your output should say "______ connected ....."  That part before connected is what we're looking for.  Im guessing it says default.

Next, lets add your new resolution.  
```
xrandr --addmode default 1280x1024
```

Restart and see if it works.  If not, we can try to create a custom xorg config file.

---

