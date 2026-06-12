---
title: "Weird X server settings with Nvidia"
date: 2010-10-19
forum: General Help
---

### Post by Werm on 2010-10-19
I discovered this: (neither show activated)

[IMG]http://icanhasimage.com/images/4z3lsaiv7di2kfy561q.png[/IMG]

Picking either to activate does this:

[IMG]http://icanhasimage.com/images/9sfut8d6cmxg8ad9brr2.png[/IMG]

I've done:
sudo dpkg-reconfigure xserver-xorg - no results

I tried reinstalling X also.

sudo apt-get remove xserver-xorg
rebooted
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
rebooted again and the problem persists. 

Terminal command: sudo nvidia-settings

> ERROR: Invalid display device DFP-0 specified on line 48 of configuration file
       '/root/.nvidia-settings-rc' (the currently enabled display devices are
       DFP-1 on werm-desktop:0.0).


ERROR: Invalid display device DFP-0 specified on line 49 of configuration file
       '/root/.nvidia-settings-rc' (the currently enabled display devices are
       DFP-1 on werm-desktop:0.0).


ERROR: The attribute 'XVideoSyncToDisplay' specified on line 55 of
       configuration file '/root/.nvidia-settings-rc' cannot be assigned the
       value of DFP-0 (the currently enabled display devices are DFP-1 on
       werm-desktop:0.0).

But the settings window still populates. 

The problem is I can't get both DVI outs on my Nvidia 8800GT to output a display. The second DVI slot just didn't do anything prior. My computer is now displaying out of port 2 but port 1 does nothing now.

The errors above reference this display

What's the best way to go about this?

I also tried 'sudo apt-get install nvidia-glx-177' which showed not found so I tried 'sudo apt-get install nvidia-glx-173' which worked but didn't fix anything.

---

### Post by Werm on 2010-10-19
Oh line 48

0/GPUScaling[DFP-0]=131073

Line 49

0/XVideoTextureBrightness=0

The last line is 54

---

