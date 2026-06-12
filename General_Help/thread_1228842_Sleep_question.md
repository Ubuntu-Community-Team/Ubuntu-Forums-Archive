---
title: "Sleep question"
date: 2009-08-01
forum: General Help
---

### Post by Tanatz on 2009-08-01
I like to have my monitor and hard drives power off after 1 hour and PC to sleep after 3 hours of idle (XP).  In Ubuntu, I see I can "put the monitor to sleep" after 60 minutes, which is fine, but when I have the computer sleep after 1 hour, it does not wake from sleep, I need to hard reboot.

In Kubuntu I noticed in the power management settings that you can either store the data on the hard disk, or in the RAM.  I did not use Kubuntu long enough to give both a shot, but is there a reason Ubuntu doesn't wake from sleep that may be tied to that?

---

### Post by Anzan on 2009-08-01
Um, sorry to ask, but did you hit the space bar?

---

### Post by Tanatz on 2009-08-01
Of course, ctrl+alt+del, esc. too.  It works in XP so it wouldn't be a BIOS issue, right?

---

### Post by Tanatz on 2009-08-02
I will give it another shot, I just don't want to risk corrupting data too many times via hard rebooting.  What would possibly prevent the OS from waking from sleep?  Something in the xorg.conf file to edit?

---

### Post by Tanatz on 2009-08-02
I went to Shut Down and hit Sleep.  I let the computer stay off for a minute, then tried to hit the spacebar, escape key, ctrl-alt-del, nothing woke it.  I tapped the power button (this is how I wake the OS in XP), the computer woke; however, the X server must freeze, because I have my desktop with graphical errors and nothing works - forced to hard reboot.  What could this be?

---

### Post by theboomboomcars on 2009-08-02
What are the specs of your computer?  And what drivers are you using? Kernel or Proprietary.

---

### Post by Tanatz on 2009-08-02
Acer AL2216W monitor
Radeon 4850...whichever drivers are installed when the restricted driver notification pops up after OS installation
GIGABYTE GA-EP35-DS3L LGA 775 mobo
Intel Core 2 Duo e8400, stock clocks

---

### Post by Tanatz on 2009-08-03
This is my xorg.conf file:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


I have just reinstalled the OS without installing the proprietary ATI drivers.  Is it true that the 4800 series of cards is not supported for 3D in Ubuntu?

---

### Post by Tanatz on 2009-08-30
So, I've gotten one step closer with this whole problem.

I've stopped using the proprietary drivers and have been using the latest driver off the ATI site (8.64).  I set the BIOS settings to fail-safe defaults, and now the PC sleeps OK (it takes a bit longer to sleep than it does in XP, but that'd be fine as long as it woke OK); however, immediately after the PC power cuts I see two quick flashes of graphical artifacting before the monitor actually cuts power too.  When hitting the power button to wake the PC, I type my password, but then I am brought back to the desktop with no taskbar or icons, just a plain desktop and my mouse icon.  Again, I am forced to hard reboot.

I have searched through aticonfig and I can't see anything about sleep that would apply to me.  Anyone else having a similar problem that can maybe shed some light?

---

### Post by Tanatz on 2009-09-03
Still trying to get this sorted out.

Here is my xorg.conf file:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
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


Any ideas?  I'm totally at a loss here.

---

