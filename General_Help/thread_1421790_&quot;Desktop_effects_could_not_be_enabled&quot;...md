---
title: "&quot;Desktop effects could not be enabled&quot;..."
date: 2010-03-04
forum: General Help
---

### Post by pingu1 on 2010-03-04
Hi!
I am having trouble getting the desktop effects enabled...
I tried booting with a live-cd.... and there it works, but not when booting from the HD.
Anybody got a solution?

I checked synaptics during the live-cd session - and tried copying the setup on the normal boot - but still - "Desktop effects could not be enabled"....

Please help....

---

### Post by pingu1 on 2010-03-04
lshw:
> *-display UNCLAIMED
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:90000000-97ffffff(prefetchable) ioport:c000(size=256) memory:c0000000-c000ffff memory:98000000-9801ffff(prefetchable)


---

### Post by pingu1 on 2010-03-04
If it works on live-cd - I guess it's some driver/package I have removed that causes it to fail starting desktop effects...? But in that case - what?

---

### Post by Fenris_rising on 2010-03-04
Not sure I can help. But Once I installed Compiz with CCSM and simple CCSM I was then able to 'activate' the effects. All this with an ATI x300 radeon and no proprietary drivers. I hope this is of some use.

regards

Fenris

---

### Post by soryu on 2010-03-04
Was Having Similar Problem. I Uninstalled Compiz Thru Synaptic,Restarted PC, Installed Compiz Thru Synaptic.Problem Solved. 

Video (Nvidia For ME) Drivers Need To Be Installed.

(problem now nvidia Drivers giving me problems):-k
i do have extra special effects tho.:KS

---

### Post by pingu1 on 2010-03-05
I would like the effects, but I do not plan to use 10 hours figuring out which drivers or what else is missing to make it work. Although I guess it has something to do with the openGL?

---

### Post by pingu1 on 2010-03-05
I'll try to remove compiz in synaptic, restart, and then reinstall compiz to see if that's it...
Are there any packages/drivers/modules in particular I should check if installed?

Thanks.

---

### Post by pingu1 on 2010-03-05
Another thing: my graphics driver seems to be working fine (2D atleast) - cause my resolution is 1280x800, which is the Maximum from what I understand for Radeon X300 on my computer (Toshiba Satellite - and older model)

---

### Post by pingu1 on 2010-03-05
Hi!
I got compiz "working" - it sort of works, but the computer doesn't handle it very well - it lags like /#&¤ and I get black borders around all windows and the desktop.....

.. ... ...

---

### Post by pingu1 on 2010-03-05
I get this in the terminal:

> compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


---

### Post by pingu1 on 2010-03-05
YEEEEEHA!!!!!
I got it working following this:
> [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

JIPPI!

---

