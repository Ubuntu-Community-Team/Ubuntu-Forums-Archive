---
title: "ATI Catalyst Control Center not saving changes at reboot"
date: 2010-02-10
forum: General Help
---

### Post by BrandonBan6 on 2010-02-10
Hello! 

I've got my ATI driver installed, now I am trying to configure it. I have a laptop plugged into a docking station with an external monitor. I would like to use the external monitor _only_

I run the admin ATI Catalyst control center (amdcccle) configuration GUI, set up my settings, just as stated above (i.e. laptop monitor off, external LCD on). Works great! Then I reboot... and I have to configure it all over again :( 

I've tried editing the settings, and then running 
```
#aticonfig --initial -f
```

But still reboot, it goes back to the default configuration. 

here are my specs:

```

#lshw -C display
  *-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3400 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:32 memory:d0000000-dfffffff(prefetchable) ioport:2000(size=256) memory:cfff0000-cfffffff memory:cff00000-cff1ffff(prefetchable)

```

Xorg.Conf 
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
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

---

### Post by BrandonBan6 on 2010-02-11
*bump*

== Additional Info, I've had this working before, however the latest kernel version update broke my configuration :(

---

### Post by NeatO7364 on 2010-02-24
I'm having a similar issue except a bit more extreme. This issue is somewhat recent and would attribute it to a kernel update as well. 

I don't use my external monitor on a regular basis but when I attempted to use it last night, it ended in frustration. Normally what I do is suspend my machine, hook up the monitor cable and when I wake the computer, it automatically feeds the external monitor. 

However this time, waking the computer froze it completely. I then did a hard restart and received warnings about no video card being detected and that Ubuntu had to be run in low-graphics mode. I checked (in low graphics mode) and fglrx was installed and active and my xorg.conf file had not changed. After several restarts, I used envyng tool to uninstall fglrx completely and reinstalled the driver using the script from ATI (that seems to no longer be available for download?) and now I am able to use the laptop monitor only. Note- using the envyng tool to reinstall the driver did NOT work. Again, if I attempt to plug in the external monitor, my laptop freezes and even if I suspend it again (by shutting the lid) and wake it again, it starts up but only into a freeze. This time a hard restart brought it back without having to reinstall the driver.

Does anyone have ANY idea what could have changed recently that would cause these symptoms? I would really like to be able to use my external monitor again...

Here is my current (working, internal monitor only) xorg.conf:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
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

And here is my previous xorg.conf file which worked perfectly to toggle between external monitor and internal monitor, depending on if the external was attached or not:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
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
	Identifier   "0-LCD"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "b" "true"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-LCD" "0-LCD"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3200 1080
		Depth     24
	EndSubSection
EndSection

```

Note: When I attempted to use the older xorg.conf (the second one listed in the post), restarting of the X server caused a crash and I was prompted to run Ubuntu in low graphics mode. I dropped to the console, replaced it with the new xorg.conf (generated by aticonfig --init yesterday) and X started back up.

Thanks for any and all help!

---

### Post by BrandonBan6 on 2010-02-24
Isn't it annoying??

I toyed with uninstalling/re-installing the driver manually enough times that I got it working. I now have two back up of Xorg.conf, one that I use when I boot up to just the laptop and one that I use when i boot up on the dock w/ext monitor. 

I followed this tutorial: 
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

Good luck!! Keep us posted if you find a good work around. If there is any more info I can provide to help you out, please do not hesitate to ask.

---

### Post by NeatO7364 on 2010-03-06
Just wanted to post a quick update. The latest kernel update (just installed about 15 min ago) also seemed to reinstall fglrx. I held my breath and crossed my fingers (as I do with every kernel update) and sure enough, I was able to boot into the new kernel without it breaking my existing video card settings!

When I plugged in the external monitor, I had to drop down to terminal but eventually just restarted the computer with the external plugged in. After restart, I'm back in business with a few minor tweaks in the ATI Catalyst program with my external monitor and my semi-dock solution. Settings are saved and I'm able to toggle back and forth between the two monitors just by sleeping the laptop (no restart required!). 

Check it out and see if the updates don't fix your video card problems as well.

---

