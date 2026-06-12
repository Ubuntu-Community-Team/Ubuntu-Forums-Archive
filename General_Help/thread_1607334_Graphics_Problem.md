---
title: "Graphics Problem"
date: 2010-10-27
forum: General Help
---

### Post by Lamez on 2010-10-27
I am not sure what I did, but when I try to boot into Ubuntu it just hangs at a black screen.

I think it happend when I was playing around with my Catalyst Control Center then the native Monitors. I think it messed up my xorg.conf file. I am not sure. Here is what I have now:

```


Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1366 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual	4166 900
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	4166 900
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection


```

Any ideas on how I get this back up and running properly? I am currently in recovery mode.

Hey, thanks for all the help!

---

### Post by Lamez on 2010-10-27
Also, when I went into safemode and replace my xorg file with a generic configuration, it worked fine, but then I could not use my ATI drivers and could not use Compiz or whatnot. So I guess a better question would be how can I use my ATI driver after switching to a generic configuration?

---

### Post by sikander3786 on 2010-10-27
Which version of Ubuntu are you using?

On newer version, Ubuntu no longer directly needs that xorg file. Make a backup of current xorg, delete the original and try reconfiguring your graphics from recovery mode.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by Lamez on 2010-10-27
I am running Ubuntu 10.10. So it is not the xorg file, then what would it be? Also how do I reconfigure from recovery mode? I know I start the recover kernal from grub, the choose the failesafe graphics mode, then what? Even if I got there, how to I reconfigure it?

---

### Post by sikander3786 on 2010-10-27
Remove the xorg as mentioned above (after backing it up) and from Recovery Mode, choose to Reconfigure graphics. If you can't find it, choose drop to root shell or something like that and,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Lamez on 2010-10-27
Thanks for your time I got it fixed with your help. I did as you said, removed the config file. Then I rebooted into failesafe mode reconfigured, then rebooted, then removed the ati drivers and reinstalled them, then rebooted and it worked!

Thanks!

---

