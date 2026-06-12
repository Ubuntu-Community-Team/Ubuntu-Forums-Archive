---
title: "Laptop Dual Monitor Issues"
date: 2010-09-02
forum: General Help
---

### Post by rasamuffin on 2010-09-02
Hi guys,

I'm a long time Windows user but recently had a laptop battery die and decided to switch it to Linux to teach myself the system.  I did a clean install of Lucid Lynx and so far I'm loving it and have managed to solve every problem I've had except for one and I am absolutely stumped: I cannot get a proper Dual Monitor display to work.  
  
On my first install I just plugged it in and attempted to use the default Monitor configuration from System<Preferences and these are the problems I got:
[LIST]
[*]When opening Wine, it would reconfigure my display so that the screens were overlapping, they had switched their left/right orientation, and shifted my open windows so they were straddling the displays
[*]When viewing any video file with any media player (I tried the default media player, VLC, and one I found in the Software Center) the video would only display if my second monitor was set to 640x480.  If I set the second monitor's resolution to anything else the video would not display on either screen.
[*]Part of the screen would become a block of alternating black blocks and part of my background and nothing would show up there.
[/LIST]  
  
If I opened the Monitor command and moved the second monitor back to the proper position in the field the screens would reset and everything would be in its proper place, but I still couldn't change the second screen's resolution.  
  
I installed a variety of drivers and a couple of different display configuration programs from the software center but nothing helped.  
  
I just did another clean install and tried to do a more "official" dual monitor set up using NVIDIA drivers downloaded straight from their site and installed from the terminal.  These are the methods I tried and the different results:

[http://ubuntuforums.org/showthread.php?t=1466150](http://ubuntuforums.org/showthread.php?t=1466150)
Tried this first, don't remember exactly what happened

[http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx](http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx)
Would go fine until sudo modprobe nvidia, at which point it would tell me the module couldn't be found.

[http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04](http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04)
Used this one, which told me to blacklist these files-vga16fb, nouveau, rivafb, nvidiafb, rivatv- which I did and then went back and tried the first two methods again, still no success.

[http://jdpfu.com:82/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://jdpfu.com:82/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver)
This one worked until I got to sudo /usr/bin/nvidia-settings at which point it told me it wouldn't load.

I then downloaded the drivers, rebooted, waited until the Ubuntu is running in low graphics mode and then exited to terminal login where I used the sudo sh NIVIDIA-Linux... command.  It would install until the end at which point I got this message: ERROR: Unable to load the kernel module ‘nvidia.ko’.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources...

I used all of the above methods with every version of NVIDIA drivers I could find recommended everywhere (96,185,195,256 and also used a terminal command that just said nvidia-current). 

So, now I'm just using my laptop by itself and I've purged everything nouveau and NVIDIA related. 
  
From what I've read, it seems that the problem with dual monitors on Lucid is because it doesn't use the xorg.conf file, right?  Most of the guides I've found to set up dual monitor include that and are for Ubuntu versions 7, 8, & 9. Would it be easier to just downgrade to one of those versions rather than continuing on with 10.04?

I'm sorry if I've posted this in the wrong thread, but this is honest to god the first time I've not been able to solve a computer problem myself and I'm not sure about proper posting protocol :) Oh yeah, if it helps, the laptop is a Dell Latitude D620, standard setup (I did browse through the Dell Help category and the Laptop Help category but didn't find anything new to try) and the monitor is an older 15" LCD, pretty generic.  

Oh yeah, the only log file I know is readily available is the NVIDIA installer one in the /var/log folder.

Thanks in advance for any advice ya'll can give.

---

