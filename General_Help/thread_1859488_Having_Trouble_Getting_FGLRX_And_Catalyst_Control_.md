---
title: "Having Trouble Getting FGLRX And Catalyst Control Center Working Properly In 11.10"
date: 2011-10-13
forum: General Help
---

### Post by Tman5293 on 2011-10-13
I just did a fresh install of 11.10 and I'm having some trouble getting the ATI graphics drivers working properly. I downloaded the drivers from AMD's website but after installing them, Ubuntu would boot to a blank black screen. I ended up uninstalling those via the command prompt. Then I tried the proprietary drivers that said post release updates and those have a bug that does not allow them to install properly. After I cleaned up that mess I installed the regular FGLRX proprietary drivers and rebooted and now it seems to be sort of working.

My problem now is this: I have two monitors. When I try to set them up as a side by side configuration with Catalyst (the default is a cloned display on both monitors) it crashes. I am currently only able to use my main display and was forced to disable my second monitor. They are different sizes and therefor different resolutions. I want to use the second display as an extended desktop just like I did in 11.04. But I can't do anything because Catalyst crashes every time I try to enable the second display as an extended desktop and not a cloned display.

Does anyone have a solution to this? I really would like to be able to use both of my monitors.

---

### Post by Tman5293 on 2011-10-13
BUMP!

Does anyone have any solutions to this?

---

### Post by panthertehcat on 2011-10-14
I'm having the same problem too. I'm yet to come across a solution.

---

### Post by 8_Bit on 2011-10-14
The post-release updates completely hosed my system. I strongly recommend avoiding them at all costs.

---

### Post by effenberg0x0 on 2011-10-14
Try post #5.
[http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati](http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati)

Regards,
Effenberg

---

### Post by panthertehcat on 2011-10-14
Additional information that may help settings-->settings manager-->Display now shows second monitor and allows me to change resolution. I'm pretty sure I couldn't do this in 11.04. Running the Xubuntu 11.10 64 bit build.

---

### Post by Tman5293 on 2011-10-14
> **effenberg0x0 said:**
> Try post #5.
[http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati](http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati)

Regards,
Effenberg

It's too bad I didn't see that while I was trying to get the driver installed. Would have saved me a lot of time. But now that it is installed and working I don't see how that will help me. I just need some way to get my second monitor working. I read something about the xorg.conf file being bugged and that if you replace it with the one from 11.04 then everything works just fine. It's too bad I don't have a copy of the 11.04 xorg.conf................

---

### Post by Tman5293 on 2011-10-14
I fixed it guys! Got my second monitor working! :D

Here's how I did it:

I opened the terminal and started messing around with aticonfig. I ended up using this code which creates as many monitors as you want in the xorg.conf file. Heads is the number of displays:

```
sudo aticonfig --initial --heads=2 --adapter=1
```

After that I rebooted and then tried to set it up with Catalyst. Catalyst recognized my second monitor and allowed me to set it as an extended desktop with the correct resolution. After I applied that, Catalyst told me that I needed to restart my PC in order for the changes to take effect. After the restart my second display was still not working. I went to Catalyst to see what was up and my monitor was there but all options for it were grayed out. I couldn't even set it as a cloned display. So I closed Catalyst and went to the Ubuntu display settings and turned on the second monitor through that and I was pleasantly surprised when it actually worked! I opened Catalyst back up and sure enough, there was my second monitor shown side by side with my primary monitor as an extended desktop.

So it turns out it was a bug in the xorg.conf file.

---

### Post by danep on 2011-10-14
@Tman- I'm glad that solution worked for you. Unfortunately, I'm still having problems. I ran ```
sudo aticonfig --initial --heads=2 --adapter=0
```, and when I rebooted my second display was totally white. I could move my cursor onto it, and the cursor would turn into a black X. Very old school :) But needless to say, totally useless. If I try to change any settings in CCC, it simply crashes without an error and doesn't save any changes. If I open the Displays manager, I don't see the second display listed.

Please help... this is seriously making me want to switch back to something that 'just works' (i.e. Windows)...

---

### Post by wanderingarticfox on 2011-10-14
you need to unlist this as solved or people will just scroll by it

---

### Post by danep on 2011-10-14
Am I able to change the prefix or can only the OP do that (I think so)? Sorry, I'm kind of new to these forums :)

---

### Post by nyteryder79 on 2011-10-14
I am having the same problem with my HD5570.  I can get dual display working, but then I loose all my transparencies and have bad lag.  What I did was:

From terminal, enter the following:
```
sudo rm /etc/X11/xorg.conf*

sudo aticonfig --initial=dual-head --screen-layout=right --output=/etc/X11/xorg.conf

sudo gedit /etc/X11/xorg.conf
```

Then I modified: 
```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection
```

To this:
```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
        Option  "Xinerama"      "on"
EndSection
```

Then ```
sudo reboot
```

But like I said, it's still not working correct because Xinerama doesn't work well with Unity/Compiz.  This is seriously frustrating me to no end, because on 11.04 (Natty) I had no issues.

---

### Post by 3602 on 2011-10-14
[http://ubuntuforums.org/showpost.php?p=10805756&postcount=4](http://ubuntuforums.org/showpost.php?p=10805756&postcount=4)

Might be slightly dated, but still works. You may read the many, uh, testimonials following my post.

Note that the Step 2 might return some different directories. You remove the ones returned and not just enter what I wrote there.

---

### Post by nyteryder79 on 2011-10-14
> **3602 said:**
> [http://ubuntuforums.org/showpost.php?p=10805756&postcount=4](http://ubuntuforums.org/showpost.php?p=10805756&postcount=4)

Might be slightly dated, but still works. You may read the many, uh, testimonials following my post.

Note that the Step 2 might return some different directories. You remove the ones returned and not just enter what I wrote there.

This doesn't help us with dual monitor support at all.  If we only had one monitor, it would work great.

---

### Post by jasidog on 2011-10-14
Same problems with dual monitor ati and what seems like a broken catalyst control center here. 

Giving up for the night. Tried so many different things I think I'll just start with another fresh install tomorrow so I know where I am starting from.

---

### Post by nyteryder79 on 2011-10-14
Ok, so I don't exactly know why this worked for me, but now I have dual monitor with my HD5570 working properly with Unity.  Here's a screenshot to show it working:

[http://i.imgur.com/4ZFfJ.jpg]("http://i.imgur.com/4ZFfJ.jpg")

Here's what I did:

Removed all xorg.conf files and started over:
```
sudo rm xorg.conf*
```

Ran Xrandr to get my monitor names:
```
xrandr
```

Results:
```
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 3840 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 479mm x 269mm
   1920x1080      60.0*+   50.0     59.9  
   1600x1200      60.0  
   1776x1000      50.0     59.9  
   1680x1050      50.0     60.0  
   1400x1050      60.0     50.0  
   1600x900       60.0     50.0  
   1360x1024      60.0     50.0  
   1280x1024      50.0     60.0  
   1440x900       50.0     59.9  
   1280x960       50.0     60.0  
   1280x768       50.0     60.0  
   1280x720       60.0     50.0     59.9  
   1024x768       50.0     60.0  
   1152x648       50.0     59.9  
   800x600        50.0     60.3  
   720x480        50.0     60.0     59.9  
   640x480        50.0     59.9     59.9  
DFP3 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 479mm x 269mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
```

Now, both of my monitors are exactly the same and run at a resolution of 1920x1080.  My left monitor is DFP3 from above, and the right monitor is DFP2.

Next, I created a new xorg.conf file:
```
sudo aticonfig --initial -f
```

Results:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Then I modified it by adding another monitor, some device options and virtual display settings:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "aticonfig-Monitor[0]-0" "DFP3"
	Option	    "aticonfig-Monitor[0]-1" "DFP2"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual 3840 1920
	EndSubSection
EndSection
```

Notice, all I did was copied the existing monitor section and changed the number at the end from 0 to 1 on the copy.  Then I added the line "Virtual 3840 1920" to the screen section.  Lastly, I added two options to the Device section, describing my two monitors.  The monitor on the left is "aticonfig-Monitor[0]-0" as it was in this file, and the copied one is "aticonfig-Monitor[0]-1", which is the right monitor.  As I stated before, the xrandr command displayed my monitor names also as "DFP3" and "DFP2".  I discovered that "DFP3" was the left monitor and "DFP2" was the right monitor, so these options were set up by matching Left with Left and Right with Right.

After editing the file, I saved it, then I called Xrandr again with the following: 
```
xrandr --output DFP2 --auto --right-of DFP3
```

Now all this seemed to do was kick me back to the login screen and once I logged back in I couldn't tell a difference.  

I opened the built-in display manager in Ubuntu, and noticed that the 2nd monitor was still disabled.  I attempted to enable it, but it would also just kick me back to the login screen.

After that I opened the Catalyst Control Center (Administrative) again, went to "Display Manager" and enabled the second monitor with "Cloned display...".  Of course this wasn't what I wanted, but I clicked apply any way.

Then I reopened the built-in Ubuntu display manager and noticed that both monitors were enabled again.  I unchecked "Mirror Displays" and hit apply.  And FINALLY, I had both monitors working again the way I wanted them to.  All I had to do was move the monitors around in the display manager.

The last thing I did was go back into the Catalyst Control Center and scale up the monitor hooked up with HDMI and set the pixel format to "RGB 4:4:4 Pixel Format PC Standard (Full RGB)" to match the DVI monitor better.

Now I know this is long, but I went through all of this to get it working for myself, so maybe it will work for you as well.  I'm no expert, and don't really know what part of this finally made everything click, all I know is that at some point it did and now it's working.

---

### Post by jasidog on 2011-10-15
I couldn't sleep, So i messed around doing some other stuff then had another bash. Seems to have fixed it. Now I'm not clever and can't be sure that my problems are the same as others but for what it's worth here's how - 

First I made a fresh install of Oneric. 

Next I followed the instructions here - [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

So that was the prerequisite preinstalls. The amd driver install commands and lastly the 2 commands relating to dual monitors.

So very similar method of driver install as already mentioned by effenberg0x0 except with a few extra steps.

Anyhow, once all that was done I was left after a reboot in a very similar position to that i had been in many times before. A working mirrored desktop but no way to change it to one desktop across both screens or change resolution etc. Ubuntu's display changer spat an error out when you tried to use it for it and Catalyst control center crashed whenever i tried to make changes.

On a whim i tried using the terminal to launch it though. The launcher had the command - 
```
amdxdg-su -c amdcccle
```

I instead used - 

```
gksudo amdcccle
```

Now when I made changes in catalyst they stuck. :)

So maybe however you install the driver from whatever source. Repos may be fine. Just running the amd comfig thing with a different command was all I needed perhaps. :confused:

---

### Post by Ellutu on 2011-10-16
Oddly, I can confirm jasidog's findings. I was having these exact same problems, further complicated by the fact that next to a second monitor I also have my TV connected (which I switch to when I watch movies). 

Up until this morning I hadn't been able to install the 11.9 drivers, aticonfig just threw an error and I'd be presented with a blank screen at the next reboot. After following [these exact instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29") though I managed to get those working, although that didn't solve the multi-monitor problem, CCC started via the launcher would still crash when pressing "apply" in the multi-display configuration (and it kept falling back to cloning my main display to my tv). 

**However**, when I ran amdcccle from the commandline using
```
gksudo amdcccle
```I would suddenly be presented with the good ol' "are you sure you want these changes to take effect?" prompt when making monitor changes, and more importantly, after restarting X, my second screen lit up :). After 3 reboots I can confirm that the monitor configuration is permanent, I'm now happily running two monitors (with different resolutions even) in the desired configuration.

[COLOR=Silver]A nasty inexplicable side-effect is that I can no longer reboot or shutdown my system using the GUI, it just throws me to the login screen (as if it only kills X). From there I can still shut down though, so it's a minor inconvenience compared to developing on one screen.

**[COLOR=Black]UPDATE[/COLOR]**[COLOR=Black]: Scratch that last remark; works just fine now, not sure what happened there.

Also I tried switching between my monitor and TV a couple of times, which seems to work as well. Second monitor to TV just works, TV to second monitor requires X-restart and, be warned, CCC immediately does that for you; no prompt there. Still works here though :).
[/COLOR][/COLOR]

---

### Post by jasidog on 2011-10-16
Ah me too - 

> 
A nasty inexplicable side-effect is that I can no longer reboot or shutdown my system using the GUI, it just throws me to the login screen (as if it only kills X). From there I can still shut down though, so it's a minor inconvenience compared to developing on one screen.

I hadn't been sure that this was related to the fix i related though. Hmm. It would be good to fix that too.

I use a little timed shutdown app on occasion that still works so I think you can still shutdown from the terminal. Not tried it yet but must be able to.

Anyway other than the the shutdown issue the only problem I'm left with is catalyst control center won#t save my preferred gamma settings. On a new boot or login they are gone. Well the gui still says it's set but it's not. Still that's definitely a separate issue as it seems to only work randomly for years when I install a new set of amd drivers.

---

### Post by jasidog on 2011-10-20
For what it's worth I seem to have found a solution to the extra problem Ellutu. 

Now I should say I have no idea what I'm doing so If you're worried at all don't follow these instructions. 


I went back to the guide we used to install the drivers and used the uninstall guide there as follows - 

```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

The first command did nothing the other seemed to work for me. So I dunno. 

Anyhow next I went to "system settings" and "Additional Drivers" and installed the ati/amd drivers there. 

**[COLOR="Red"]Not the post-release updates[/COLOR]** They wouldn't install when i tried first go around before all this mess.

After that i rebooted and with a huge hang mid process but the reboot seemed to work. On next boot I still had an extended dual monitor setup, correct resolutions. I tested rebooting again and it worked better though with quite a hang at the desktop before seeming to proceed normally. 

I'm hoping this will clear up for smoother reboots yet and assuming a plain old shutdown will now work too though I haven't tried one yet.


I don't know but I'm thinking the cleanest solution would have been to used the ubuntu provided ATI drivers in the first place, then just use the "gksudo amdcccle" command to make catalyst control center work. I can't know that without trying but it's my guess.

---

