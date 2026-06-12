---
title: "change color depth in ubuntu 10.04?"
date: 2010-05-08
forum: General Help
---

### Post by Joe-ubunt on 2010-05-08
Does anyone know how to change the color depth from 24 to 16 in Ubuntu 10.04? I'm running an older computer and my computer needs to run at 16 to view videos. I just have an integrated Sis 630/730 64mb graphics card.
 
In Ubuntu 9.10 and Linux Mint 8 I just added lines to the blank xorg.conf file to change the color depth but this doesn't work in Ubuntu 10.04. When I restart the computer the system the screen freezes up with the caps lock and scroll lock flashing until I manually shut it down. I have to then use recovery to get back in and change the xorg.conf file to blank. 
 
I'm sure there is somehow a way to lower the color depth in Ubuntu 10.04. I've searched and searched the net but can't find a way.

---

### Post by TheNerdAL on 2010-05-08
This might help: [http://ubuntuforums.org/showthread.php?t=268150](http://ubuntuforums.org/showthread.php?t=268150)

---

### Post by Joe-ubunt on 2010-05-08
> **TheNerdAL said:**
> This might help: [http://ubuntuforums.org/showthread.php?t=268150](http://ubuntuforums.org/showthread.php?t=268150)

Thanks but it doesn't help. 10.04 doesn't want to honor my created xorg.conf script. This is the script that always worked for 9.10 and linux mint:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    16
EndSection

Maybe a different script for Ubuntu 10.04 is needed? There has to be a way to force color depth down to 16.

---

### Post by Joe-ubunt on 2010-05-12
Ok, I got my system to create a new xorg.conf file and changed color depth and tried numerous other xorg.conf files but it still does the same thing (freezes at desktop- Kernal panic). At best I can get the 16 depth change to work every other boot. It'll freeze and then I hard restart and it will boot perfect into 16 depth. Then when I restart the system it will freeze at desktop with caps and scroll lock flashing. Kind of strange that it will work perfect 50% of the time and yet freeze the other 50%.
 
Did Ubuntu 10.04 change anything xorg wise to no longer allow a forced reduction in color depth? Is this some kind of bug? I went back to Linux Mint 8 and it works flawless with the forced 16 depth. Ubuntu 9.10 also worked flawless with the forced 16 depth. 
 
Other than not being able to lower the color depth, Ubuntu 10.04 really worked great on my computer. It is just my computer can't handle 24 depth with my lcd monitor too well (choppy video playback, slower system, etc). 
 
Has anyone successfully changed color depth to 16 in Ubuntu 10.04? I don't want to waste my time if a color depth change is impossible in 10.04.

---

### Post by Belfry on 2010-05-13
Yes.

Let the new X-server set up the "device" section.  Below is the contents of my _entire_ xorg.conf:

```

Section "Monitor"
	Identifier	"Default Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Default Monitor"
	DefaultDepth	16

SubSection		"Display"
	Depth		16
	Modes		"1024x768"
EndSubSection

EndSection
```
One can look at a picture like [this]("http://inapcache.boston.com/universal/site_graphics/blogs/bigpicture/yushu_04_26/y01_23045545.jpg") to check if 16-bit color is in fact enabled (16 bit will show "layers" of halos.)

---

### Post by Joe-ubunt on 2010-05-14
> **Belfry said:**
> Yes.

Let the new X-server set up the "device" section.  Below is the contents of my _entire_ xorg.conf:

```

Section "Monitor"
	Identifier	"Default Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Default Monitor"
	DefaultDepth	16

SubSection		"Display"
	Depth		16
	Modes		"1024x768"
EndSubSection

EndSection
```
One can look at a picture like [this]("http://inapcache.boston.com/universal/site_graphics/blogs/bigpicture/yushu_04_26/y01_23045545.jpg") to check if 16-bit color is in fact enabled (16 bit will show "layers" of halos.)

Thanks for your help. I tried your xorg.conf but it did the same thing at desktop- freeze up with the caps and scroll lock flashing until I had to hard restart. It's good to know others have the system working flawless in 16 depth. 

An easy terminal command to check depth is: 
xdpyinfo | grep "of root" 


So far the best xorg.conf file for my system is this:

Section "Device" 
	Identifier	"Configured Video Device" 
	Driver		"sis" 
EndSection 

Section "Monitor" 
	Identifier	"Generic Monitor" 
	Option		"DPMS" 
	HorizSync	30-71 
	VertRefresh	50-160 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"Configured Video Device" 
	Monitor		"Generic Monitor" 
	DefaultDepth	16 
	SubSection "Display" 
		Depth		16 
		Modes		"1280x1024" "1024x768" 
	EndSubSection 
EndSection 

The only problem is that I HAVE to move my mouse when the startup reaches the desktop or else it will go into kernal panic. Once I am past the "scare area" everything works as normal in 16 depth. I don't understand why I have to move the mouse to avoid kernal panic at startup?

No other xorg.conf file I tried would even work at 16 depth no matter what I did. I'm thinking maybe I have to add something else to my xorg.conf.

Anyone have any suggestions as how to fix this?

---

### Post by Joe-ubunt on 2010-05-15
Ok, I got it working now. I found that if I chose to login manually instead of auto it didn't freeze. Then I uninstalled HAL from synaptic and set the login back to auto in System/Admin/Login.
Now it boots perfect in 16 depth and also boots faster. So far I didn't have any kernal panics at start so I believe all is well. 

As for the xorg.conf file, any basic file that changes the depth to 16 works. The xorg.conf files I was using wasn't the problem after all. 

I don't know if it was setting the login to manual and then resetting it back to auto that worked or removing HAL but now it boots fine in 16 depth.

---

