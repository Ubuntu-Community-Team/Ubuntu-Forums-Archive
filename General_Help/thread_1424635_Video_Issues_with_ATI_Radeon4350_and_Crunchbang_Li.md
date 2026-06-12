---
title: "Video Issues with ATI Radeon4350 and Crunchbang Linux 9.04"
date: 2010-03-08
forum: General Help
---

### Post by JC99 on 2010-03-08
I did a fresh install of crunchbang linux, both 32 and 64 bit and get the same result.  I have a strange video issue, see the pic.  The desktop is the correct size coming out at 1080 or 720p to my Sony 60" TV via a DVI to HDMI cable.  The desktop is the right size but all text on the screen is around 8-10" tall.  If I open a terminal I can barely type since only a few words will fit on the screen.  It is truly strange.

All I did after a fresh install is load this driver package:

sudo apt-get install xorg-driver-fglrx

and then:

aticonfig --initial - prior to this the screen was scrambled after reboot.

I have also tried (on a different fresh install) to load the downloaded ATI 10.2 package, the 9.4 and the 9.8 package and they all result in the same issue.  I think I need to modify the xorg.conf or some other settings but am not sure where to begin.  Can anyone please offer some insight into how to get this to work correctly?  

I was using an Nvidia card before but it has bad overscan issues, and the gui would lock up every few days.  I got this ATI card since they do not overscan as bad on my TV and I hope it fixes the lockup issues I've had with this nvidia card on this system, linux MCE, and Fedora.

In the pic below I clicked on the network icon to get the popup menu.  All text is this big whether I open a terminal or anything pops up.  

Thanks!

[IMG]http://i138.photobucket.com/albums/q266/jmcrtp/photo.jpg[/IMG]

---

