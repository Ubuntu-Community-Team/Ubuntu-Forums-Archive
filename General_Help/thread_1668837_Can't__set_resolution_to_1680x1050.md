---
title: "Can't  set resolution to 1680x1050"
date: 2011-01-16
forum: General Help
---

### Post by dchalhub' on 2011-01-16
Hello,

The native resolution from my LCD monitor is 1680x1050, but the list of "NVIDIA X Server Settings" only allow me to set it to maximum 1360x768. The monitor is conected via VGA cable and it is recognized as CRT-0. When I run the 'xrandr' command from terminal, it shows:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1680 x 1050
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0

In Windows the monitor works fine with 1680x1050 and my video card is Geforce 9600GT

Please help me...

---

### Post by fabricator4 on 2011-01-16
Can you select a higher refresh rate in the monitor dialogue?  Doing so may enable higher resolutions.

Failing this, you might have to manually enter the allowable sync range in the xorg.conf file.  I have to do this for a couple of machines that share a monitor/keyboard through a switch, since it can't autodetect the range for the monitor itself through this setup.

Chris.

---

### Post by dchalhub' on 2011-01-16
> **fabricator4 said:**
> 
Failing this, you might have to manually enter the allowable sync range in the xorg.conf file.  I have to do this for a couple of machines that share a monitor/keyboard through a switch, since it can't autodetect the range for the monitor itself through this setup.



Can you tell me how to do this?

Thank you

---

### Post by fabricator4 on 2011-01-16
Well it seems like your video card is being recognised OK, so I won't go into that (someone may correct me).  When changing the xorg.conf file, the first thing you should do is make a backup copy.  Open a terminal window and do the following:

```
cd /etc/X11 
sudo cp xorg.conf xorg.backup
```

If you don't already have an xorg.conf file, it will give an error that it can't find it.  Don't worry about it, I've noticed that later releases (10.04 on maybe) have dropped the need for a default xorg.conf but you _do_ need to make sure you changed to the correct directory  (note: directories are case sensitive!).

Next thing you need to do in that same terminal window is edit/write the xorg.conf file. (if you close the terminal window you'll have to cd to /etc/X11/ again).

```
sudo nano xorg.conf
```

Next, to enter the correct sync ranges you need to know these values for your monitor.  You can normally find these in the instruction manual that came with the monitor, under "specifications" or you can maybe get the specs off the manufacturer's site by googling the brand and model of the monitor.  I'll show you my xorg.conf which will give you a fair idea of what you need to do:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Samsung 1100p"
	Horizsync 30-110
	Vertrefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Samsung 1100p"
	Device		"Configured Video Device"
EndSection

```

Note the formatting of this file.  The tab formatting may not be critical but it helps to keep everything straight.  The section/end section, capitalization etc certainly _is_ critical.

Note that xorg.conf is a low level configuration file.  If you get it wrong Ubuntu won't be able to open the graphical interface but will give you the option of logging in to a text only terminal screen.  If this happens you'll have to reverse what you did by deleting the xorg.conf file or copying xorg.back back to the xorg.conf:

```

cd /etc/X11
sudo cp xorg.back xorg.conf

```

or (to ReMove it)

```

cd /etc/X11
sudo rm xorg.conf

```

whichever is appropriate.  Unfortunately this is the only way I've found to get around the problem if xorg cannot get this information from the monitor for some reason. Windows remembers the last read parameters from the monitor and will re-use them, xorg does not.

Chris

---

