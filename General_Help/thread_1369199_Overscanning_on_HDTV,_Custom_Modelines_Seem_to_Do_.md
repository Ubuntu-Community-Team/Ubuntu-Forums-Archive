---
title: "Overscanning on HDTV, Custom Modelines Seem to Do Nothing"
date: 2009-12-31
forum: General Help
---

### Post by Maltor124 on 2009-12-31
I have to admit I am way over my head in this. I have an HDTV, specifically a Panasonic TH-50PX60U. It is 1080i, with a native resolution of 1366 by 768, according to the manual. It has a vertical refresh rate of 60Hz, and a horizontal of ~40-45Hz. GPU is a NVIDIA 7100GT embedded into a mini-ITX motherboard from Zotac, using an nForce 630i chipset (If you need the exact model for that I can dig it up).

As the title indicates, I am having some ovserscanning issues on this setup. Ubuntu sets the resolution to 1280 by 720 at 60Hz from device recognition, which doesn't create a blurry image, but makes it so only about half of the bottom and top toolbars are visible, and the Show Desktop and Trash icons on the bottom toolbar being completely cut off.

I have a fairly clear idea of how this is fixed: by editing the xorg.conf file for the X Server, and putting in your own settings to make it have the correct resolution. However, herein lies my true issue. No matter what I do, the custom settings in xorg.conf don't seem to do anything. It certainly doesn't apply them at startup, the NVIDIA X Server Settings manager doesn't show any new items, nor does the built in Ubuntu Display manager, which says it doesn't recognize my monitor, anyway.

Attached below is my current xorg.conf. It's probably all screwed up at this point, so any help would be greatly appreciated. :(

```
Section "Monitor"
Identifier "PANASONIC TV"
HorizSync 15.0 - 46.0
VertRefresh 59.0 - 61.0
Option "DPMS"
Option "IgnoreEDID"
#DisplaySize 720 405
#ModeLine "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
 Modeline "1360x765_60.00"  84.40  1360 1424 1568 1776  765 766 769 792  -HSync +Vsync
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce 7100 / nForce 630i]"
Driver "nvidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV18 [GeForce 7100 / nForce 630i]"
Monitor "PANASONIC TV"
Option "FlatPanelProperties" "scaling = centered"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1360x765@60"
EndSubSection
SubSection "Display"
Depth 24
Modes "1360x765@60"
EndSubSection
EndSection
```NOTE: In other threads I found that the best resolution I could reasonably get would be 136 by 765 @ 60Hz, which is why the xorg.conf has those values.

The gtf command in Terminal was used to generate the modelines.

EDIT: xvidtune -show confirms that the settings do not change.

---

### Post by shairozan on 2009-12-31
Hey, 

Have you installed the drivers for Nvidia? I've only compiled them from source, but they normally add a menu to system -> administration or system -> preferences that allows you to edit the xorg file to match the settings for the card. 

I had this issue recently where I was using a slimline desktop to run HDTV out into a 42 inch plasma. My issue was that the image was always getting cut off, regardless of resolution. There's a setting in that menu that allows you to tweak stuff for HD output such as screen centering, size, etc. I'd say check that first.

---

### Post by Maltor124 on 2009-12-31
I'm using the latest NVIDIA Canonical recommended drivers (the version 185s), straight from the repository. I tried some newer ones directly from NVIDIA's site, too, but they didn't help. However I didn't poke around with the setting on the newer ones much; is there anything that might be helpful on newer versions?

Also if the settings you are talking about are GPU-Scaling method from the NVIDIA X Server settings, I already played around with those a lot. No dice.

---

### Post by Maltor124 on 2010-01-02
Bump.

Anyone? D:

---

### Post by marcusrab on 2010-01-15
Ok, I had been fighting this exact same issue for the past week..
 
I had went through numerous xorg configs to no avail.. experiencing the same thing you were, the simple solution?
 
Uninstall the 185 drivers.. and then update to the new 190 drivers.. there is a slider bar in the nvidia settings panel for those drivers that allows you to correct overscan.. I believe its called "overscan compensation"
 
I have a nvidia 9800gt video card and a 50" Panasonic TC-P50X1 and the drivers worked perfectly!
 
 
Hope this helps!
 
here is the guide I followed to upgrade
 
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)
 
Now, it says for Karmic Users:
 
**For Ubuntu Karmic Users**
Use the following command to add PPA
[INDENT]sudo add-apt-repository ppa:nvidia-vdpau/ppa
 
 
 
I didnt do this.. I followed the Jaunty instructions and just put Karmic inplace of the word jaunty, then followed the remainder of the instructions
 
 
The bottom of this page helped with overscan
 
[http://www.mythtv.org/wiki/Working_with_Modelines](http://www.mythtv.org/wiki/Working_with_Modelines)
 
annnd..
 
I got my modelines from here :
 
[http://www.mythtv.org/wiki/Modeline_Database#Panasonic](http://www.mythtv.org/wiki/Modeline_Database#Panasonic)
 
 
 
Hope this helps!
[/INDENT]

---

### Post by WoGGo on 2010-01-18
I am in a similar boat to you guys, however...

I have the 190.45 Nvidia drivers, with the overscan compensation sliding bar.
I can slide the bar to my desired point and all is fine... but I cannot save the xorg.conf, however, the setting remains for the duration of my session.

My problem then comes once I reset.

The overscan problem returns, but all I have to do to fix it is go to Nvidia X Server Settings.. not even having to adjust the slider again?!?

---

### Post by RuinKaos on 2010-02-18
> **WoGGo said:**
> I am in a similar boat to you guys, however...

I have the 190.45 Nvidia drivers, with the overscan compensation sliding bar.
I can slide the bar to my desired point and all is fine... but I cannot save the xorg.conf, however, the setting remains for the duration of my session.

My problem then comes once I reset.

The overscan problem returns, but all I have to do to fix it is go to Nvidia X Server Settings.. not even having to adjust the slider again?!?

I believe you have launch nvidia-settings with sudo to save the settings to the xorg.conf

Open up a terminal and type the command below: 

sudo nvidia-settings

Should launch the Nvidia control panel and saving should work.

---

### Post by efflandt on 2010-02-18
I know nothing about xorg.conf (since there is none by default in Ubuntu 9.10), but I suspect that the name for a Modeline, and tne name for a Mode have to match.  A "1360x768@60" mode would not pay attention to a modeline named "1360x765_60.00".

---

### Post by z3ds on 2010-03-10
I'm also having the same problem with the overscan compensation slider.

I use "sudo nvidia-settings" to save what I did with the overscan compensation slider but when I restart , the slider goes back to zero again.

---

### Post by Psychotic.EGG on 2010-03-22
I have the same problem only I can seem to install any driver versions newer than 185. I went to manually install the newest from Nvidia but after downloading them gedit couldn't unpackage them. and when I tried Marcusrab's option the terminal stated could not find 190. Help?

---

