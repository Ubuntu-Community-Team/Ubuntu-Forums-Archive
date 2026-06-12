---
title: "How to add a new resolution?"
date: 2010-11-10
forum: General Help
---

### Post by janderpola on 2010-11-10
I´m using Ubuntu 10.10 32 bits with ATI Mobility Radeon HD 4500 Series on a Dell Studio 1558, and my problem is i can´t set a properly resolution.

I can set it to 1920x1080, wich in most cases is to high that makes everything so little, and the next properly resolution (same proportions) is 1280x720, wich i find too big sometines, so i´m triying to set an intermediate resolution, in this case 1600x900 wich keeps the proportions of the screen, because the rest of the resolutions doesn´t keep the proportions.

I´m using propietary (fglrx) driver, and here is what i have tried:

- Adding a "Modes 1600x900" section in xorg.conf file, wich looks like this:

> Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[2]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
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
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x900"
	EndSubSection
EndSection


That makes nothing, because i can´t see the 1600x900 anywhere to try it.

- I have tried with xrandr, following [this tutorial]("https://wiki.ubuntu.com/X/Config/Resolution#Adding undetected resolutions"), where i make this:

> plaos@plaos-laptop:~$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 1920 x 1920
LVDS connected 1280x720+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9 +
   1680x1050      59.9 +
   1400x1050      59.9 +
   1280x1024      59.9 +
   1440x900       59.9 +
   1280x960       59.9 +
   1280x800       59.9 +
   1152x864       59.9 +
   1280x768       59.9 +
   1280x720       59.9*+
   1024x768       59.9 +
   1024x600       59.9 +
   800x600        59.9 +
   800x480        59.9 +
   720x480        59.9 +
   640x480        59.9 +
DFP1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)


> plaos@plaos-laptop:~$ cvt 1600 900
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync


> plaos@plaos-laptop:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync


After this, when i exec xrandr again i get this after CRT2 discon...

> CRT2 disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0xe2)  118.2MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   56.0KHz
        v: height  900 start  903 end  908 total  934           clock   59.9Hz


And if i try to add the resolution, i get this error:

> plaos@plaos-laptop:~$ xrandr --addmode LVDS 1600x900_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28


- I finally tried using aticonfig, where manual section says:

>   --resolution=Screen#,W1xH1,W2xH2,W3xH3,...
        Set the modes for the specified screen.  You may specify several
        resolutions separated by commas.
        Screens start at 0.  You can use 1 for dual-head


So when i try this, i get the next:

> plaos@plaos-laptop:~$ sudo aticonfig --resolution=0, 1600x900
[sudo] password for plaos: 
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.


I am desperated, which metod i should follow, and where i am doing something wrong?

---

### Post by janderpola on 2010-11-11
Would be easier using the open-source driver?

---

### Post by gillza on 2011-04-08
Hey I have a similar problem. I'm trying to set up a TV through VGA to output 1600x900 ( currently 1360x768 ) following the same guide. I have built in ATI x1400 running on an open source driver and that is what I get:


```
$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27
  Current serial number in output stream:  27

```

---

### Post by Krytarik on 2011-04-08
> **gillza said:**
> Hey I have a similar problem. I'm trying to set up a TV through VGA to output 1600x900 ( currently 1360x768 ) following the same guide. I have built in ATI x1400 running on an open source driver and that is what I get:


```
$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27
  Current serial number in output stream:  27

```
What if you simply proceed!?

---

### Post by gillza on 2011-04-08
Well actually I wanted to write about that.

Ran:
```
$ xrandr --addmode VGA-0 1600x900_60.00
$ xrandr --addmode LVDS 1600x900_60.00

```

and now I have: 
```
$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 3360 x 1050
VGA-0 disconnected (normal left inverted right x axis y axis)
   1600x900_60.00   59.9  
LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1680x1050      60.2*+   60.0  
   1600x1024      60.2  
   1400x1050      60.0     60.0  
   1280x1024      59.9     60.0  
   1440x900       59.9     59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
   1600x900_60.00   59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
```

And I can see that resolution in Gnome Desktop Manager for the monitor and for the TV. Tv for some reason does not support it even though a windows machine connected to it with this output was ok.

---

### Post by Krytarik on 2011-04-08
> **gillza said:**
> And I can see that resolution in Gnome Desktop Manager for the monitor and for the TV. Tv for some reason does not support it even though a windows machine connected to it with this output was ok.
Meaning that when you try to apply the video mode to the TV via the GUI, it fails?

It seems you need to pass the TV's specs to the xserver by setting up a proper xorg.conf, try following this guide:
[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

---

### Post by gillza on 2011-04-08
No it works. Tv just cant handle it coming from Linux vs Coming from Win... Refresh rate probably?

I'll try the guide tonight and post back the update. Thank you Kind Sir!

---

### Post by Krytarik on 2011-04-08
> **gillza said:**
> No it works. Tv just cant handle it coming from Linux vs Coming from Win...
Hey, what is this here, a guessing game!? Turns the TV screen black or what?

---

### Post by gillza on 2011-04-08
> **Krytarik said:**
> Hey, what is this here, a guessing game!? Turns the TV screen black or what?

I assumed when I say TV cant handle it is understood that it either displays some error or just turns black. Mine turned black. If there would be any useful information in he error message I'd post it here.

I'll post the update after I'm done changing xorg.conf and testing it out. Don't have access to TV right now.

---

### Post by Krytarik on 2011-04-08
> **gillza said:**
> If there would be any useful information in he error message I'd post it here.
You can check "/var/log/Xorg.0.log" and "~/.xsession-errors" for related error messages, respectively the *.old files depending on if you check them within the running session or at the next.

---

