---
title: "upgraded, 9.10 and now have 800x600 resolution"
date: 2009-11-08
forum: General Help
---

### Post by rhythmiccycle on 2009-11-08
I just upgraded to ubuntu 9.10

and now my screen resolution is at 800x600. I can't work with this. 

I went to display settings but 800x600 is the max.
How do i make it bigger?

I read some other posts, but I don't understand everything whats going on.

the monitor I have is:
> 
ViewSonic VE175 17" LCD

with an optimum resolution of 1280x1024, brightness of 250 nits and contrast ratio of 550: 1

Synchronization Range - Vertical 50 - 75 Hz 

Synchronization Range - Horizontal 30 - 80 kHz 

Brightness 300 cd/m² 

Color Depth 24-bit (16.7M Colors)


I tried adding this to xorg.conf:

```

Section "Monitor"
    Identifier     "VE175"
    HorizSync       30.0 - 80.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "GPU"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GPU"
    Monitor        "VE175"
    DefaultDepth    24
EndSection

```

but then when I try those specs my monitor says:
> 
out of range
H:74.9khz
V:59.9hz


please help I don't know what to do

right now the xorg.conf I'm using looks like this:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"

	SubSection "Display"
		Depth	1
		Modes	"1280x1024" "800x600"
	EndSubSection
EndSection

```

I added the SubSection "Display" part my self hoping that would help, but it has no effect.

---

### Post by dummy910 on 2009-11-08
You need a video card driver listed in your /etc/X11/xorg.conf file.

I don't even use monitor resolutions in my xorg.conf file, just the video driver and the old 19" crt monitor I type this response from will go all the way to 1600x1200.

Here's my xorg.conf for a reference point:
> #   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
EndSection
[SIZE="1"]Note: always make a backup of system files when tweaking like this ;)[/SIZE]

---

### Post by rhythmiccycle on 2009-11-08
thanks for the reply,

when i type $ lspci | grep VGA in to a terminal i get

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

so what do I type into xorg.conf?

i see under device you have "ati" do I need to write "Integrated Graphics Controller"??

I also see you have a Section "Module", that I don;t have at all. Can I just add that one to mine the same way you have it?

---

### Post by plnnightsky on 2009-11-17
I have the exact same problem after upgrading from 9.04 to 9.10.  I also have the same video card.  

Did you get answer on how to resolve it?  I tried modifying xconf.org and added higher resolution and then run sudo dpkg-reconfigure -phigh xserver-xorg.  This had no effect

---

### Post by Yellow Pasque on 2009-11-18
It might help if people posted their /var/log/Xorg.0.log
It could be something trivial like Xorg setting the virtual screen size too low.

---

### Post by arnab_das on 2009-11-18
you need to install your graphics drivers. if ur having nvidia, u could check this:

[http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/](http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

---

### Post by darkksyde on 2009-11-18
in the upgrade, your kernel was updates so you need to reinstall your video drivers. You can do this by going to System > Administration > Hardware Drivers, and selecting your video card and clicking activate.

---

### Post by arnab_das on 2009-11-18
> **darkksyde said:**
> in the upgrade, your kernel was updates so you need to reinstall your video drivers. You can do this by going to System > Administration > Hardware Drivers, and selecting your video card and clicking activate.

generally the website has the latest versions compared to ubuntu hardware drivers.

---

### Post by Giblet5 on 2009-11-18
You have the wrong frequencies listed.

That is the only explanation.

Try using this for your xorg.conf:
```
Section "Monitor"
    Identifier     "VE175"
    HorizSync       74.54
    VertRefresh     60
EndSection

Section "Device"
    Identifier     "GPU"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GPU"
    Monitor        "VE175"
    DefaultDepth    24
EndSection
```

Then you can try bumping the VertRefresh toward 75 to eliminate flicker.

That will give you 1600x1200.

---

### Post by plnnightsky on 2009-11-20
Here is the Xorg.0.log file or at least a portion of it.  Most of what is mentioned is beyond me.  It did correctly identify the Intel graphics card:
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==)drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): EDID for output VGA1
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
 intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): EDID for output VGA1
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
...
It repeats this for all refresh rates including hsync.


It then has the following:
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 800x600
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 800x600
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
) Loading sub module "fb"

(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 800x600
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 800x600
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
) Loading sub module "fb"

As I mentioned before it work properly under 9.04.  I did not install any video drivers then.  I am willing to try with 9.10, but cannot find any which seem to work.

The video card is an Intel on board 945G.

---

### Post by wojox on 2009-11-20
Try:

```
aptitude show xserver-xorg-video-intel
```

See if it's installed.

---

### Post by wojox on 2009-11-20
If so put this in Device

```

Section "Device"
      Identifier"Intel Corporation 82915G/GV/910GL IntegratedGraphicsDevice"
      Driver          "i810"
EndSection

```

---

### Post by plnnightsky on 2009-11-20
It is installed.  Is this a concern?


Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810
      Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810
           (< 2:1.9.91-1), xserver-xorg-video-i810-modesetting,
           xserver-xorg-video-intel-modesetting     (< 2:1.9.91-1), xserver-xorg-video-i810-modesetting,
           xserver-xorg-video-intel-modesetting

---

### Post by plnnightsky on 2009-11-20
I replaced the section as suggested, and ended up with a flashing screen and no GUI.

Is there something which can probe the graphics card to see what it is?  It is an Intel of some kind and i though it was 945 as well.

---

### Post by plnnightsky on 2009-11-27
I have not found and answer on how to fix the problem.  Nobody does anybody else seem to have an answer, soon I will dump ubuntu and go with something else

---

