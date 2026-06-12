---
title: "frame rates"
date: 2006-02-11
forum: General Help
---

### Post by njzillest on 2006-02-11
i used to play Americas Army on Windows XP, it ran perfect, no problems.
Now im running AA on Ubuntu (Gnome) and the FPS seems to be very low.. is there a way to tweak the FPS? Im using a toshiba R/10 tablet that has a toshiba graphics card, witch 64 mb independind memory. I Have 512 mb of ram.


thank you so much.

---

### Post by dcstar on 2006-02-11
[QUOTE=njzillest]i used to play Americas Army on Windows XP, it ran perfect, no problems.
Now im running AA on Ubuntu (Gnome) and the FPS seems to be very low.. is there a way to tweak the FPS? Im using a toshiba R/10 tablet that has a toshiba graphics card, witch 64 mb independind memory. I Have 512 mb of ram.


thank you so much.[/QUOTE]
Various posts in the Games forum and others as well you can search on, basically related to getting Direct Rendering working on your particular hardware.

Run this to see if it is:

glxinfo

---

### Post by cotcot on 2006-02-12
I had to install acceleration (fglrx driver) for my graphics card (ATI) : [http://www.student.dtu.dk/~s971652/ati_radeon.shtml](http://www.student.dtu.dk/~s971652/ati_radeon.shtml) to obtain the fram rate required to run flightgear. Maybe you could find something comparable for your Toshiba or search on fglrx.

---

### Post by visionary on 2008-01-13
Maybe you could try the following which i harvested from some other websites which helped me greatly with Flightgear in Gusty....

1)When you start flight gear, consider starting with the following options in your command.... (You can read more from here [http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html](http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html) )

> --control=mouse
> --disable-intro-music
> --disable-random-objects
> --disable-sound
> --disable-hud-3d
> --disable-specular-highlight
> --fog-fastest
> --model-hz=60
> --geometry=800x600
> --visibility=10000.0
> --fov=50
> 
> --prop:/sim/rendering/static-lod/detailed=500
> --prop:/sim/rendering/static-lod/rough=5000
> --prop:/sim/rendering/static-lod/bare=15000
> --prop:/environment/clouds/layer[1]/coverage="clear"
> --log-level=alert

That actually improved a little.....Now for the biggest improvement i go was to to do the following.....

2) downloaded driconf (sudo apt-get install driconf)

3)Then edit device section of /etc/X11/xorg.conf to show as

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "ati"
[B]BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "AGPFastWrite" "true"
Option "EnableDepthMoves" "true"
Option "GARTSize" "64"
Option "AGPSize" "64"
Option "backingstore" "on"
Option "UseInternalAGPGART" "no"[/B]
EndSection


Though i am using Nvidia card, i added those lines (in bold)  in my xorg.conf file.

Now restart your system and enjoy your flight gear.
Hope that helps!

Cheers!

---

### Post by phillips321 on 2008-01-13
depending on the 3d card for your laptop u might need to install the drivers, fingers crossed u have an ati or nvidia, things are much easier then (System-Administration->Restricted Drivers Manager)

---

