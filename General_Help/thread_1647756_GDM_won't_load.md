---
title: "GDM won't load"
date: 2010-12-17
forum: General Help
---

### Post by Kylen on 2010-12-17
Hello
The gnome desktop won't load. Instead, I keep getting the login screen. If I try to reboot, start X in failsafe mode, it is also not possible to see anything. If I boot in recovery mode, command line, and startx I see only the mouse pointer, and I can change desktops (ctrl alt arrow), but nothing more, no menus or anything, I can't even open nautilus.
I think this happened after I changed the desktop theme to orta, so it may be related to that.
Any ideas? thank you

---

### Post by Kylen on 2010-12-18
This is the error message when I try to open with failsafeX:

(EE) RADEON(0): Acceleration initialization failed
(EE) GKX Error: Can not get required symbols

---

### Post by Krytarik on 2010-12-18
What a video card/chip are you using, obviously ATI, what model?
Did you install any driver?

---

### Post by I'mGeorge on 2010-12-18
> **Kylen said:**
> Hello
The gnome desktop won't load. Instead, I keep getting the login screen. If I try to reboot, start X in failsafe mode, it is also not possible to see anything. If I boot in recovery mode, command line, and startx I see only the mouse pointer, and I can change desktops (ctrl alt arrow), but nothing more, no menus or anything, I can't even open nautilus.
I think this happened after I changed the desktop theme to orta, so it may be related to that.
Any ideas? thank you

change to another desktop or into your command line environment and uninstall that theme and see how this goes. 

By the way can you play 3D games or run graphical demanding applications ? If you do than it must be the theme if you don't than either you've didn't properly installed the drivers for your video card or maybe you've didn't installed them at all.

---

### Post by Kylen on 2010-12-18
graphics model: 
ATI Redwood [Radeon HD 5600 Series]

I think I had fglrx proprietary drivers installed, but I did not use 3D games or applications.

When I start failsafeX- Ubuntu is running in low-graphics mode. Your screen, graphics card could not be detected correctly. You will need to configure these yourself. But even trying to run in low-graphics mode does not work.
TY

---

### Post by Kylen on 2010-12-18
I removed packages starting with "orta" including the "orta-theme" and it still does not work.
TY

---

### Post by Kylen on 2010-12-18
By the way, I can boot up the ubuntu live CD with gnome, with all the menus and things, as expected, so it must not be hardware related.

---

### Post by Krytarik on 2010-12-18
Is there a /etc/X11/xorg.conf in place right now?

If so, rename it, e.g.:
```
sudo mv xorg.conf xorg.conf.backup-18.12.2010
```
and try to create a new default one:
```
sudo dpkg-reconfigure xserver-xorg
```
Then again try to
```
startx
```

---

### Post by Kylen on 2010-12-18
Thank you for the suggestion.
Is there a /etc/X11/xorg.conf in place right now?
There was not.
I issued the command
sudo dpkg-reconfigure xserver-xorg
but no xorg.conf was created.
At least not in the /etc/X11/ directory.

After start x I againg get just a background with the mouse.

It should be related to this? Any other way to create a working xorg.cong, or other suggestions?

---

### Post by Krytarik on 2010-12-18
Are you running the Netbook Edition?

Anyhow, as there is apparently no way to get to your desktop, try installing the fglrx-driver provided by the Ubuntu-X-Team:

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

check if the fglrx-driver is already installed
```
dpkg -l | grep fglrx
```
if so, remove it
```
sudo apt-get remove --purge fglrx
```
install the new one
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install fglrx
```
reboot.

---

### Post by Kylen on 2010-12-19
I am not running the netbook edition.
Now I lost my wireless connection, but my main concern right now is to get gnome working. So I downloaded the fglrx_8.801*i386.deb from 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages)
 after removing the fglrx I had previously installed like you said.
Unfortunately it didn't solve the problem.
Thanks again.

---

### Post by Krytarik on 2010-12-19
Try
```
sudo aticonfig --initial -f
```
to write a new xorg.conf, altough this should have been done already by the installation of the driver.

If that doesn't help either please post the xorg.conf.

---

### Post by Kylen on 2010-12-19
The aticonfig command did not work, as you expected.
Here is my xorg.conf: 

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

---

### Post by Krytarik on 2010-12-19
What version of Ubuntu are you running?

Try those:

- set "radeon" or "radeonhd" instead of "fglrx".

- set the modules in your xorg.conf like in the example:
[http://wiki.cchtml.com/index.php/Troubleshooting#An_Example_of_a_working_Xorg.conf](http://wiki.cchtml.com/index.php/Troubleshooting#An_Example_of_a_working_Xorg.conf)

- set the options according to
[http://wiki.compiz.org/ATI%20with%20AIGLX](http://wiki.compiz.org/ATI%20with%20AIGLX)

- set "HorizSync" and "VertRefresh" according to the ouput of
```
xvidtune
```
  Press "Cancel"!

---

### Post by Kylen on 2010-12-19
I am running Ubuntu 10.04.1 
I tried the options in the pages you mentioned and it still does not work. More, the output of xvidtune is just: 
Error: Can't open display: 
Thanks for keeping up with this.

---

### Post by Krytarik on 2010-12-20
Try this instead, I tested it (only in virtual console):
```
DISPLAY=:0.0 xvidtune
```EDIT: Why did you loose your wireless connection, is this an external problem? Could it be related?

---

### Post by Kylen on 2010-12-21
DISPLAY=:0.0 xvidtune
Error: Can't open display 0.0

Maybe it's related to the loss of wireless, I don't know.

---

### Post by Krytarik on 2010-12-21
> **Kylen said:**
> DISPLAY=:0.0 xvidtune
Error: Can't open display 0.0

Maybe it's related to the loss of wireless, I don't know.
Ok, sorry, I tested it only in a virtual console, had my doubts too.

Fortunately "hwinfo" delivers the info as well:

[http://packages.ubuntu.com/lucid/hwinfo](http://packages.ubuntu.com/lucid/hwinfo)
[http://packages.ubuntu.com/lucid/libhd16](http://packages.ubuntu.com/lucid/libhd16)

```
sudo hwinfo --monitor
```

You may also try to start the desktop with a new user, in case of a faulty config:
```
sudo useradd NEW_USER
sudo passwd NEW_USER
```

---

### Post by Krytarik on 2010-12-21
Try the "extmod" tip here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1)

and the tip here (altough the given BusID should be sufficient):
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Black_Screen_when_supposed_to_see_login_screen](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Black_Screen_when_supposed_to_see_login_screen)

And please post the output of
```
fglrxinfo
```Try replacing "fglrx" with "radeon" or "radeonhd" in xorg.conf as driver.

---

### Post by Kylen on 2010-12-21
I tried to install the packages from these two files but I got some warning that the package could not be found.

I also tried to add a new user, but I just got the background and the mouse pointer.

Anyway, I just realised with the link you gave I may have been doing some stupid installation of packages for maverick, when I have lucid... 
Thank you for your suggestions, but I think will start to make backups of everything of importance and install ubuntu again soon.

EDIT: When I do that I will mark this thread solved. If in the meantime you think you may have a solution, please post it.

---

### Post by Krytarik on 2010-12-21
I also think that -given what you said- re-installing isn't such a bad idea.

PS: Both packages have to be installed at the same time, or at least libhd16 first, because hwinfo depends on it.

---

### Post by Kylen on 2010-12-21
I just saw the post 19. I tried those suggestions and it didn't work, and also fglrxinfo said "unable to open display".
Reinstalling is starting to look a very good idea.
Thank you very much!

---

### Post by danske on 2011-01-21
Just wanted to bump this thread and thank Krytarik as well as Kylen for getting some good info out there.

I just put in a new ati card over my integrated graphics , and lost my display on a machine dual booting windows 7 and 10.10.  I went to the root with networking prompt and purged all the old fglrx stuff, backed up my xorg.conf, got the new drivers and did the initial aticonfig, and I'm back in business :).  Thanks guys

---

