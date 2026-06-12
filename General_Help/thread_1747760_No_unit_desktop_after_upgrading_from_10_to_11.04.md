---
title: "No unit desktop after upgrading from 10 to 11.04"
date: 2011-05-03
forum: General Help
---

### Post by Khar136 on 2011-05-03
Hi,

When I was using Ubunutu 10, I updated the ATI drivers from their web site and the installation failed. There is no uninstall for it that actually works. So, very annoyed, I switched to the VESA driver by editing xorg.conf as shown below.

I just upgraded from Ubuntu 10 to 11.04 and when it booted up it told me that I do not have hardware to run the Unity desktop. Even on a restart the login menu shows the selected desktop as "Ubuntu" (no classic or anything though my desktop looks just like it did in Ubuntu 10).

After upgrading to Ubuntu 11 it seems to have switched to a proprietary ATI graphics driver which actually seems to work very well. Except, no Unity desktop.

If I click System, Administration, Additional drivers it shows one driver and says that it is enabled and in use. The driver is "ATI/AMD proprietary FGLRX graphics driver" and in the description it says "3D-accelerated proprietary graphics driver for ATI cards".

Is there a way to explicitly turn on Unity or ask it why it doesnt want to run?

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5670]

$ /usr/lib/nux/unity_support_test -p
Segmentation fault

I do not really care which driver I use. I have been told there is a new driver included in Ubuntu 11 that supports my video card. Is that the driver I listed above or is thee another that I can activate somehow. What shall I do? I just want Unity to work.

Try disable this driver? Will it automatically pick up some default? Do I have to delete or do something to xorg.conf as well?

Is there a way to tell Ubuntu "forget whatever video card driver or configuration is in place and go back to the default for a new install"? I have tried "dpkg-reconfigure xserver-xorg" but all it does is ask for a password and then does nothing. Everyone says to run this buts its never done anything for me.

/etc/X11$ cat xorg.conf
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
Subsection "Display"
	Modes		"1280x1024" "1024x768" "1280x960" "1600x1200"
EndSubsection
EndSection

---

### Post by Khar136 on 2011-05-03
:P Ok I just ran "sudo dpkg-reconfigure xserver-xorg" though I do not know if that did anything or not. Then I clicked "System, Administration, Additional drivers" and clicked "Remove" on the proprietary ATI driver. Then restarted.

And viola! Unity came up and it works fine and everything is snappy and the desktop is showing the proper resolution that it did long long ago before the proprietary ATI drivers first started failing to install.

:popcorn::D:popcorn::D

My advice to anyone here is: Stay away from the proprietary drivers if you can. There no uninstall for one.

My /etx/X11/xorg.conf now looks like this:

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
EndSection

Woohoo!!!!

---

