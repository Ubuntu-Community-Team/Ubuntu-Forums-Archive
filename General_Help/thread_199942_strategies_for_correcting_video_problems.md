---
title: "strategies for correcting video problems?"
date: 2006-06-19
forum: General Help
---

### Post by linuxguiri on 2006-06-19
what are some things i can try to correct video problems? for the past month i've been having problems with artifacts on my lcd screen. 

strangely, the problem didn't exist for months before though. i don't know if an update might have caused it, but i don't know how i would go about figuring it out. upgrading to dapper didn't fix it and i've tried reconfiguring xserver.

are there alternative drivers i can try?

i have an ati radeon mobility 7500 video driver.

---

### Post by pellgarlic on 2006-06-20
did it start suddenly? did you make any major changes to you system around the time it started? do you have a dual-boot setup? (to check if it's ubuntu, or the laptop screen itself. if you don't have a dual-boot, you could try a live cd - knoppix or something). also, i think the "vesa" driver works with ati cards, although i'm not positive. even if it does, i'm pretty sure it doesn't provide 3d acceleration and all that jazz.

---

### Post by linuxguiri on 2006-06-21
thanks for your response.

yeah, it was pretty much out of the blue and I'm pretty sure I hadn't made any major changes. i first started to notice it on my last.fm player, but i don't even have that installed anymore and it still happens.

yes, I have a dual-boot system and the problem doesn't exist when I boot to windows so it's not the screen.

i can try the vesa driver, but it'd be nice to be able to take advantage of 3d acceleration, etc. how do i go about specifying one driver over another?

---

### Post by pellgarlic on 2006-06-21
you could first of all, make sure you have the newest version of the ati drivers installed. as i have an nvidia card, i'm not sure whether they are in the repos or not. if you have the newest version already, perhaps a previous version will work better? if they are in the repos, there should be a couple of versions available - check and see.

if none of the above help, follow these instructions to try the "ati" or "vesa" drivers (although you will not have 3d acceleration, if the artefacts disappear, the trade-off might be worth it?):

N.B. before doing this, print these instructions out, or write them all down - this may result temporarily in having no gui!

ok, to change driver, first open a terminal window.
first, we'll backup your "xorg.conf" file (which contains info about your graphics setup):

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

now we'll open it for editing:

```
sudo gedit /etc/X11/xorg.conf
```

look for the bit that says "Section "Device" " where your graphics card should be listed. there will be a line that says "driver = "something" " change that "something" to say "ati". now save the file, and close gedit. 

now you have to restart "X" to test the change. first, logout. once you are at the gdm login screen, press "ctrl-alt-bkspc". this restarts "X".

the screen will go black momentarily, and if the change has worked, the login screen will return. login, and check if the artefacts have gone. if they have, smile :)

if the login screen does not come back, and you get a blue screen with white writing saying something like "x-server cannot be started", don't worry - we can revert to the xorg.conf we backed up before. if you are asked if you want to view error logs, you can if you want - sometimes rooting through these can provide info about what went wrong. once you have viewed these, or just said "no", you should be at a "command prompt" like this:

```
login:
```

enter your login name, and press enter, then enter your password and press enter. now, we will replace the xorg.conf we juast modified with the one we saved earlier. type:

```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

now, type:

```
startx
```

and the gui should be back.

try again from the start, but in gedit, instead of using "ati" as the driver, use "vesa".

---

### Post by pellgarlic on 2006-06-21
ok, the "3d acceleration" drivers for ati cards is called "fglrx", and it's in the repos. check to see if you have the newest version, and if not, update it.

---

### Post by dresnu on 2006-06-21
Unfortunately fglrx doesn't work for radeon 7500. You 'll have to use either the radeon or the ati driver which are both open source. Edit xorg.conf and change the Driver under the Device Section to "radeon" or "ati".
I suggest you use the ati driver, which in the dapper version supports direct rendering, as I get better performance than the radeon.

---

### Post by linuxguiri on 2006-06-22
thanks for the help!

neither the "ati" nor "radeon" drivers worked. but with the "vesa" driver there are no artifacts (although there's a slightly disconcerting garbled screen when x windows loads).

when i was editing xorg.conf i noticed the monitor is set to "generic monitor" with no specific sync or refresh settings. it's actually an lcd xga. could this be affecting the ati and radeon drivers? i noticed some of the xf86config-4 files posted online for my model are using ati and radeon drivers.

---

### Post by linuxguiri on 2006-06-22
Found this similar bug on launchpad: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/34435/+index](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/34435/+index)

Switching to radeon driver and turning "RenderAccel" option to "off" got rid of artifact problem and the strange video issues don't occur at startup as they did with vesa driver.

The relevant sections of my xorg.conf file are now:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"AGPMode"	"4"
	Option		"RenderAccel"	"off"
EndSection

Section "Monitor"
	Identifier	"LCD XGA 1024x768"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

---

### Post by pellgarlic on 2006-06-22
glad you found a solution :)

---

