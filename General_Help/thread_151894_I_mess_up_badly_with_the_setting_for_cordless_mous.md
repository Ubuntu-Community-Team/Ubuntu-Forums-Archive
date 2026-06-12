---
title: "I mess up badly with the setting for cordless mouse"
date: 2006-03-28
forum: General Help
---

### Post by gladd8tor on 2006-03-28
Hi ... I am a newbie and I have a fresh installment of Ubuntu BB 5.10 version , I try to follow the description from this link 

[http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech](http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech)

this is my info 
I: Bus=0011 Vendor=0002 Product=0002 Version=003d
N: Name="PS2++ Logitech MX Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

what I done was as suggestion from the link , this below

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/#mice"
#mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

And added this below that 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB Receiver"	
	Option		"Dev Phys"		"usb-*/input1"
	Option		"Device"		"/dev/input/ts0"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"9 10"
EndSection

Now when I went to reboot I got this error 

Failed to start the X server ( your graphical interface ) It is likely that it is not set up correctly .Would you like to view the X server output to diagnose the problem 

                                   YES / NO  >>> Click yes and get this 

X Window system version 6.8.2 ( Ubuntu 6.8.2-77 20051010174523 root @vernadsky. buildd) 
Release Date : 9 February 2005
X Protocol version 11, revision 0, relese 6.8.2
Build operating system : Linux ubuntu 2.6.122-686 #1 Sat Mar 11 16:22:51 UTC 2006 i686 
Build date : 10 October 2005 before reporting problems , check [http://wiki.X.Org](http://wiki.X.Org) 
to make sure that you have the latest version .
Module loader present OS Kernel : Linux version 2.6.12-10-686 ( buuild@terranova) ( gcc version 3.4.5 20050809 ( prerelease) ( Ubuntu 3.4.4-6ubuntu 8.1)) #1 Sat Mar 11 16:22:51 UTC 2006 T 
Markers: (--) probed , (**) from config files (==) deault settings 

SORRY for this to be so long but , Could someone please explain where I went wrong ? 

Thanks

---

### Post by trent dillman on 2006-03-28
Add this to your xorg.conf to keep it from failing.

Section "ServerFlags"
   AllowMouseOpenFail
EndSection

I don't know about setting up your mouse, though.

---

### Post by gladd8tor on 2006-03-28
Hi ... What area do I place that suggestion ? Or does it mater ? Thanks

---

### Post by trent dillman on 2006-03-30
Try at the very end...like I said though, this will just prevent X from crashing, it won't fix the mouse issue.

---

