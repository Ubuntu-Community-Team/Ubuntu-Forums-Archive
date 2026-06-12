---
title: "Nvidia GeForce 7300 GS not recognized by 12.04"
date: 2012-05-05
forum: General Help
---

### Post by Easy Limits on 2012-05-05
I find it odd that 12.04 does not recognize my video card.  See attached screen shots.  Is this a bug?  As far as I can tell everything is installed correctly and the video card is working fine.  The Nvidia X Server settings are fine also.

---

### Post by Easy Limits on 2012-05-07
Bump.

---

### Post by alphacrucis2 on 2012-05-15
> **Easy Limits said:**
> Bump.

What do you get from this:


```
sudo lshw -C display
```

---

### Post by Easy Limits on 2012-05-15
*-display               
       description: VGA compatible controller
       product: G71 [GeForce 7300 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e1000000-e1ffffff memory:d0000000-dfffffff memory:e0000000-e0ffffff

---

### Post by ak47s on 2012-05-21
Got exactly the same problem, i didnt get it with OpenSuse i think. i think it was the 185 drivers 

*-display               
       description: VGA compatible controller
       product: GF110 [GeForce GTX 570 HD]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff


Already did  
```
 sudo sh nvidia.run -f
```its running the latest drivers 295.3x

Unity 3d renders without problems but Gnome 3 not.

I only get a classic view with unity theme

I am running two monitors on pys:0 and turned xinerama off (twinview)

"Ubuntu without Gnome is like Woman without B0ob$" - Ak47S

---

### Post by ak47s on 2012-05-21
I also get this while : ```
 System:~$ gnome-shell --replace
Window manager warning: Missing composite extension required for compositingWindow manager warning: Log level 8: g_object_ref: assertion `G_IS_OBJECT (object)' failed


```

---

### Post by ak47s on 2012-05-21
Ok so my whole intention was to run Gnome 3 since the drivers were properly installed by Nvidia thus Xorg. That Ubuntu doesnt sees it doesnt really matter i guess.

I got it working and here is what i did
```
sudo vim /etc/X11/xorg,conf
```

And change the bottom line that says
```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

Into

```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Cheers, i hope people with similar Gnome 3 problems use this solution.

---

### Post by Michael Longval on 2012-07-20
Thanks for that tip.  Worked great with my old Acer laptop.

Cheers.

Mike

---

