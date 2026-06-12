---
title: "Dual Monitors Problem after upgrading to 11.04"
date: 2011-05-03
forum: General Help
---

### Post by datapirate42 on 2011-05-03
I just upgraded to 11.04 from 10.10 (which I had to reinstall after upgrading to 11.04 beta and attempting to install gnome 3 but I digress) and now my monitors are permanantly stuck on clone.

When I go into monitor preferences and uncheck same image in all monitors I get a popup error

"**The selected configuration for displays could not be applied**
requested position/size for CTRC 148 is outside the allowed limit : position=(1680,0), size=(1680,1050) maximum=(1920,1920)"

What I want to do is set one monitor to 1680x1050 and the other to 1920x1080 but basically it is telling me it needs a resolution higher than this seemingly arbitrary number...

in my past adventures with this I was able to change some Xorg.conf file to increase this maximum but I think that was 10.10 and now I cannot find a file that has that setting in it.

If anyone knows where it is, or knows some other simple work around I'd greatly appreciate the help

---

### Post by Amused2Death on 2011-05-03
I feel your pain,

I can only get "monitor unknown" with a resolution of 3200x1080, 50hz.
I cant change anything and it point blankly refuses to detect any of the two monitors.

As the main monitor is only 22" i doubt that the resolution is reporting correctly, i think its actually around 1600x?? and the 17"is probably around 1024x??. Thats what they were before the upgrade.

In fact the only thing i can do under monitors now, is "show monitors in panel" and this is because i've got rid of unity and am running in classic mode. I needed some familiarity whilst i tackle the upgrades problems

---

### Post by steeloavenger on 2011-05-03
Hey everyone i found out how to solve the dual monitor issue. Although its for Nvidia it may give the ATI people a route to help themselves too. [http://www.youtube.com/watch?v=g6EYc4bJ6JQ](http://www.youtube.com/watch?v=g6EYc4bJ6JQ)
It worked for me and i felt a little silly that it was so easy. I hope it helps.

deuces

---

### Post by datapirate42 on 2011-05-03
Yeah unfortunately I am on an ATI, and I know my problem is basically just a stupid setting that needs to be changed

I was looking around and got to this 
```
boehme@boehme-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, _**maximum 1920 x 1920**_
DFP1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+
   1400x1050      60.0 +
   1440x900       59.9 +
   1280x800       60.0 +   75.0  
   1152x648       60.0 +
   1280x1024      75.0     60.0  
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0 +
   1680x1050      60.0* 
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)

```

I think I just need to change that value I bolded... anyone know how?

---

### Post by Amused2Death on 2011-05-04
:oops::oops::redface:

I remind myself of a Monty Python sketch... "How sweet to be an idiot"

---

### Post by datapirate42 on 2011-05-05
Sooooo... nobody knows how this works? Does that mean the best solution is just to go back to 10.04 and wait until they actually make Natty usable and not just pretty?

---

### Post by ashokcm on 2011-05-16
Similar to nVidia, there is ATI Catalyst Control Center (Administraive) for ATI. It is available from System -> Preferences

---

### Post by elpaxoudis on 2013-03-26
Well i checked this: my _maximum_ is **1680x1680** so i put to _monitor1_ **800x600** and to _monitor2_ **800x600** _total_ of: **1600x1200** and it worked show indeed we have to tweek that _maximum_...

---

### Post by QIII on 2013-03-26
Old thread.  Back to sleep.

---

