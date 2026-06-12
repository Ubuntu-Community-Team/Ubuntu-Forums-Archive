---
title: "Resolution too high, can't see panel"
date: 2011-10-07
forum: General Help
---

### Post by marsrise on 2011-10-07
After setting up a new monitor I increased the resolution and now the panel cannot be seen nor accessed.  Of course that means no terminal, now system settings, I'm stuck.  Can anyone suggest keystrokes, anything to allow me to reset the monitor resolution?  I'm using Karmic.  Many thanks.

---

### Post by dcstar on 2011-10-07
> **marsrise said:**
> After setting up a new monitor I increased the resolution and now the panel cannot be seen nor accessed.  Of course that means no terminal, now system settings, I'm stuck.  Can anyone suggest keystrokes, anything to allow me to reset the monitor resolution?  I'm using Karmic.  Many thanks.

Boot up in Recovery mode and select a basic graphics option, then reset the resolution to something low and do a normal reboot to set it back.

---

### Post by marsrise on 2011-10-07
Thanks David.  I tried to do as you suggested but there didn't seem to be any change in the resolution or image when choosing a different display option in recovery.  The problem is that while I can modify the settings while not connected to the external monitor (it's a laptop), since the machine doesn't detect the external display while disconnected, none of the adjustments can be modified that will attach to the connected monitor, and I cannot make any changes because I can't see icons in the panel, there is no "applications," places," nor "system" to click on.  If I could find a shortcut keystroke that would get me into the monitor settings through the GUI while connected to the external monitor, then I think I could make it work.

---

### Post by marsrise on 2011-10-08
I've figured out a way to get back to where I was at the start.  Not ideal but it works for now.

---

### Post by WasMeHere on 2011-10-08
Start a terminal with *ctrl + alt + t* and run
```
gnome-display-properties
```
or if you have nvidia graphics driver
```
/usr/bin/nvidia-settings
```

This way I think that you can access the tool to set your screen resolution. A command line option is to use *xrandr*.
```
man xrandr
``` should also do the trick.
```
       Xrandr  is  used  to set the size, orientation and/or reflection of the
       outputs for a screen. It can also set the screen size.

       If invoked without any option, it will dump the state of  the  outputs,
       showing  the existing modes for each of them, with a '+' after the pre&#8208;
       ferred mode and a '*' after the current mode.

```
for example
```
xrandr -s 1280x1024     # or
xrandr -s 1920x1080
```

Good luck
Olle

But maybe the problem would be solved by adjusting the screen with its buttons or knobs (usually at the bottom of the frame).

---

