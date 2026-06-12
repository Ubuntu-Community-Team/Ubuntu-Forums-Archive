---
title: "No Touchpad Tab in Mouse Settings"
date: 2010-08-19
forum: General Help
---

### Post by Charbs on 2010-08-19
Over the past week Ive read every single post on these forums that have to do with a trackpad, xorg.conf setting, and SHMConfig. Yet none of it seems to work for me.

My touchpad on my Sony VAIO EB series laptop seems to work fine. And it even has vertical scrolling on the right side of it. But there is no trackpad tab in the mouse settings. So I cant enable and advanced mouse settings. My xorg.conf is blank and empty, and creating an fdi file with SHMConfig true/on doesnt help either. 

So I tried installing the Touchpad softare to see if that helps. But it just gives the error:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Im running 10.04, 32bit. Nothing ive tried seems to be working. What gives?

This is the output of xinput list:

charbs@charbs-laptop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard

---

