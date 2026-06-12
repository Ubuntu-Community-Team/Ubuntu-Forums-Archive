---
title: "Requesting help with monitor resolution"
date: 2011-10-16
forum: General Help
---

### Post by angus1000 on 2011-10-16
Ubuntu experts,

I've read over some of the posts on this forum but am still having problems. I just installed 32-bit Ubuntu 11.10. I am unable to configure my monitor to run at 1280x1024, 32-bit color, and 75Hz, which is what I use when running Windows. Under System Settings -> Displays my monitor is listed as Unknown. The maximum resolution under the pull-down tab is 1024x768. I'd like to use the settings previously mentioned, most importantly getting the resolution up to 1280x1024.

My monitor is a Dell M782 which is a CRT. My video card is an ATI HD4800 - Sapphire I believe. I just installed the latest x86 Linux drivers from the AMD/ATI website.

I tried the xrandr command which returns the following:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  

Also, I don't appear to have /etc/X11/xorg.conf file (not sure what this is about)

I suspect that I may to do some kind of xrandr --newmode command but have no idea how to configure all the params.

If you guys could walk me through this, I'd really appreciate it. Thanks.

-Angus

---

