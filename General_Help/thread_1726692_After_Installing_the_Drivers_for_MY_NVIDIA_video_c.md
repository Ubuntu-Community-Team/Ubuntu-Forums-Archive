---
title: "After Installing the Drivers for MY NVIDIA video card it changed my resolution?"
date: 2011-04-11
forum: General Help
---

### Post by meinsternlicht on 2011-04-11
My boyfriend gave me a new video card, I reinstalled my computer with Ubuntu 10.10 and the resolution was fine. I turned off my computer last night and when I turned it on today it's back to everything being huge and the screen resolution being 640 x 480. Then when I try to change it, it says my video card isn't supported. All I want to do is revert back to my stock video card in my computer and remove the nvidia one since obviously ubuntu isn't working with it. I don't know how to do that. Any help would be appreciated.Thanks!

---

### Post by TeoBigusGeekus on 2011-04-11
Have you installed the restricted drivers for your card?
Look in Administration>System>Additional Drivers.

---

### Post by meinsternlicht on 2011-04-11
I did that, that is what changed the resolution. :(

---

### Post by TeoBigusGeekus on 2011-04-11
What is your graphics card?
Can you post us the output of
```
lshw -C display
```
?

---

### Post by meinsternlicht on 2011-04-11
description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:22 memory:fb000000-fbffffff memory:d0000000-dfffffff memory:fc000000-fc01ffff

---

### Post by TeoBigusGeekus on 2011-04-11
Give 
```
gksu nvidia-settings
```
from terminal.
Can't you change the resolution from nvidia's tool?

---

### Post by meinsternlicht on 2011-04-11
The only two choices it gives me is 640x480 and 320x240. It wont' let me change it to 1024 by 768

---

### Post by Cavsfan on 2011-04-11
See if this helps:
To bring up a list of "supported" resolutions:

[B]sudo xrandr -q
[/B]
Sets resolution to 1280x800

**sudo xrandr -s 1280x800**

---

### Post by meinsternlicht on 2011-04-11
amaranth@amaranth-ER912AA-ABA-SR1810NX-NA620:~$ sudo xrandr -s 1280x800
Size 1280x800 not found in available modes
amaranth@amaranth-ER912AA-ABA-SR1810NX-NA620:~$ sudo xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   640x480        50.0     52.0  
   320x240        51.0  
   1024x768       52.0*    50.0  
amaranth@amaranth-ER912AA-ABA-SR1810NX-NA620:~$ sudo xrandr -s 1024x768
amaranth@amaranth-ER912AA-ABA-SR1810NX-NA620:~$ sudo xrandr -s 1024x768
amaranth@amaranth-ER912AA-ABA-SR1810NX-NA620:~$ 
amaranth@amaranth-ER912AA-ABA-SR1810NX-NA620:~$

---

### Post by meinsternlicht on 2011-04-11
Really, I just want to get rid of it and revert back to my stock card. Is there a way to do that.

---

### Post by TeoBigusGeekus on 2011-04-11
Well of course. 
First, delete your xorg.conf file
```
sudo rm /etc/X11/xorg.conf
```
Then power off your pc, unplug it, open its case, take out the card and replace it with your old one.

After a quick googling, news aren't well for Nvidia FX5200 anyway.

---

### Post by Cavsfan on 2011-04-11
Didn't **sudo xrandr -s 1024x768** set it to the right resolution?

---

### Post by realzippy on 2011-04-11
> **meinsternlicht said:**
> Really, I just want to get rid of it and revert back to my stock card. Is there a way to do that.

system=>administration=>additional drivers

you will find an uninstall option.

............................................................................

the nvidia driver won't work with fx 5200;fiddling around with xrandr
with not working nvidia drivers  -and suggesting this- never makes sense)

---

### Post by Duncan Williams on 2011-04-11
I have the same videocard (fx 5200). It worked fine in 10.1 at 1900 by 1080 on my 24" monitor.
It doesn't work as well with 11.04 (natty) but I am using it now at 1900 by 1080 albeit with a minor workaround.

---

### Post by Duncan Williams on 2011-04-12
after todays updates, it sorted itself out and works heaps better.

---

### Post by Duncan Williams on 2011-04-12
after reboot the resolution is like great. nuff said...

---

### Post by realzippy on 2011-04-12
@ DWilli
..guess you do *not* use the proprietary nvidia driver?
If you do,which version?

---

### Post by Duncan Williams on 2011-04-12
No proprietory drivers after last install of natty.
I was advised in additional drivers of:
[I]experimental 3D support for NVIDIA cards.
This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.
You need to restart your desktop session after installation.[/I]

Thats when my pc would boot to a blank screen in ubuntu mode.
(I used failsafe graphics mode to get into gnome)

After installing updates yesterday.
There were amongst the updates NVIDIA related and nouvea and experimental.

After a few reboots:
I am now booting straight into unity mode ubuntu with full support for my fx5200 card. and no noticeable problems.

The resolution is superb on my 24" monitor > the best it has been, photos are now clearer than any previous installation of either windows or ubuntu.

---

