---
title: "laptop to projector not working"
date: 2009-11-21
forum: General Help
---

### Post by rpm13 on 2009-11-21
I am running Ubuntu 8.4 on a Fujitsu lifebook laptop
I am unable to get it to transmit (from VGA) to a projector (or a terminal for that matter)

Note it works in windows. ie if I press appropriate hotkey Fn+w
(w is the function key with a monitor icon) it turns the external display on and off.
I tried installing hotkeys. It makes the function keys for dimming and brightening work but not the external VGA.
I tried all possible settings in BIOS + the physical switch next to the VGA port -- No luck.

I understand that the low level infrastructure for this kind of stuff has changed in recent ubuntus.  But I dont want to go through an upgrade cycle (right now) if I can help it (and after that will it work?)

---

### Post by NoBugs! on 2009-11-21
You shouldn't need to upgrade for it, Ubuntu supports second monitor although it doesn't immediately switch to it.

There's a lot of good info [here]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") on how to configure displays for Linux.
If you don't want to use a shell command to switch screens, you could also use a gui tool such as [this]("http://www.google.com/search?q=grandr") or [this]("http://sourceforge.net/projects/projectortool/") to switch the second display on.

---

### Post by rpm13 on 2009-11-22
> **NoBugs! said:**
> You shouldn't need to upgrade for it, Ubuntu supports second monitor although it doesn't immediately switch to it.

There's a lot of good info [here]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") on how to configure displays for Linux.
If you don't want to use a shell command to switch screens, you could also use a gui tool such as [this]("http://www.google.com/search?q=grandr") or [this]("http://sourceforge.net/projects/projectortool/") to switch the second display on.

Neither grandr nor the projectortool did anything
When I run xrandr I get
```

$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+   75.1     70.1     60.0* 
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +   60.0* 
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

```
Note the 0mm x 0mm in the LVDS
Ive also tried dpkg-reconfigure -phigh xserver-xorg

---

### Post by NoBugs! on 2009-11-22
If xrandr isn't working it is probably a graphics-driver problem. What is the graphics-card brand/model?
Have you tried checking for system updates then restarting?

---

### Post by rpm13 on 2009-11-22
> **NoBugs! said:**
> If xrandr isn't working it is probably a graphics-driver problem. What is the graphics-card brand/model?
Have you tried checking for system updates then restarting?

lshw gives me
```

 *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon Mobility U1
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8

```

Some other info you need?

---

### Post by NoBugs! on 2009-11-24
Have you tried the latest ubuntu release to see if this has been fixed?
You could try it from the livecd, see if the graphics card output works, and if it has been fixed, go to places -> hard drive and view your files on the projector.

---

### Post by rpm13 on 2009-11-25
> **NoBugs! said:**
> Have you tried the latest ubuntu release to see if this has been fixed?
You could try it from the livecd, see if the graphics card output works, and if it has been fixed, go to places -> hard drive and view your files on the projector.

This is an idea -- I will try it when I get the time. 
Thanks.

---

### Post by rpm13 on 2010-01-25
> **NoBugs! said:**
> Have you tried the latest ubuntu release to see if this has been fixed?
You could try it from the livecd, see if the graphics card output works, and if it has been fixed, go to places -> hard drive and view your files on the projector.

Well I upgraded to karmic and the projection worked -- thanks
I would mark this as solved but there are still one or two things that windows does better:
[list=1]
[*]Turn on or off the projector with a hot key
[*]Projector detected at run time. Currently ubuntu needs to be rebooted after the vga connection is made
[/LIST]

---

