---
title: "desktop resolution reset"
date: 2009-10-18
forum: General Help
---

### Post by Ace_NoOne on 2009-10-18
When I booted up my laptop ([HP Compaq 2510p - specs]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01057682&lang=en&cc=us&taskId=101&prodSeriesId=3355633&prodTypeId=321957")) this morning, the desktop resolution was limited to 1024x768 (normal is 1280x800), with no way to reset it in the Display Preferences dialog.

Unfortunately, none of the [thread]("http://ubuntuforums.org/showthread.php?t=1067110")s or [HOWTO]("http://ubuntuforums.org/showthread.php?t=83973")s I found helped me fix the problem - so I'm at wit's end.

Here's my current *xorg.conf* (the latest iteration, with a few additions to the basic configuration as per the guides mentioned above):
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"	"true"
	Option		"MigrationHeuristic"	"greedy"
	Option		"Tiling"				"false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline	"1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes	"1280x800_60.00"
	EndSubSection
EndSection

```
(Modeline via *$ cvt 1280 800*)

Additional info:
```

$ xrandr -q
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0

$ sudo lshw -C display
  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```
Any help would be extremely appreciated!

---

### Post by liame on 2009-10-18
hi, same problem here in a msi-wind u100

i remember that yesterday night there was an update of some intel package
maybe is related?

---

### Post by Ace_NoOne on 2009-10-18
> **liame said:**
> i remember that yesterday night there was an update of some intel package
maybe is related?
Now that you mention it, I too ran a system update yesterday - */var/log/apt/term.log*:
```

Setting up libdrm-intel1 (2.4.14-1ubuntu1~xup~2) ...
[...]
Setting up xserver-xorg-video-intel (2:2.9.0-1ubuntu2~xup~1) ...

```
Any way to roll back?

---

### Post by liame on 2009-10-18
:( i don't know how to roll back, sadly...

i tried changing the xorg.conf and lxrandr & grandr but didn't help.
i am horrible stuck in 800x600 resolution and the output of running xrandr in terminal is 

```
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

```

the horror the horror...

---

### Post by michaelvoss on 2009-10-18
Same problem here..only worse.

Mine boots up to a black screen (seems as if monitor is off).

I can see the boot up screen and the progress bar, but after that it goes dark.

I did the update yesterday too. Seems like something broke the resolution.

So how in the heck to I fix it when I can't even see anything on the screen.

---

### Post by liame on 2009-10-18
:) hey!!!! i found a solution!!!

ok, short explanation:
i went to synaptic, looked for the xserver-xorg-video-intel & found that indeed it was the 2.9.0. version ---> then i forced version to the first one under the 2.9.0 ---> apply ----> reboot 

& there it was, my beautiful beautiful resolution back
:)

edit: now that it's there, i'll write how i got there:
i found this [thread]("http://ubuntuforums.org/showpost.php?p=8120994&postcount=1215")
the posts number 1215 & 1216 did the click for me.
i got x-update unchecked on my sources.list (i'll wait a few days and see what happened before getting it back) 
hope it helps. 
(on the way to this i learn a little more about adding resolutions to xrandr :) )

---

### Post by Ace_NoOne on 2009-10-19
Thanks liame, that actually worked:
```
sudo aptitude install xserver-xorg-video-intel=2:2.6.3-0ubuntu9
```
I had forgotten that I was using the X-updates repository.

michaelvoss: Can you boot up in safe (single-user) mode? Alternatively, you could try pressing CTRL+ALT+F2 to get a console, then enter the command above to install the correct drivers.

---

### Post by MikeDK on 2010-01-09
Running lucid X86_64 here, and it runs very nice, only the intel GM965 carddriver could be a little faster, but overall its running very nice.

only thin i could be without is the freeze on lid close. cant get the screen to turn on again after lid close.

kind regards mikedk

---

### Post by MikeDK on 2010-01-09
one thing i want to know here, why are you using the uxa accelmethod and in the same time your using the exaoptimization.

why dont you set the accelmethod to exa?

kind regards mikedk

---

### Post by Ace_NoOne on 2010-01-10
> **MikeDK said:**
> one thing i want to know here, why are you using the uxa accelmethod and in the same time your using the exaoptimization.

why dont you set the accelmethod to exa?
It's basically cargo-culting; I didn't really know what I was doing...
However, I'm now using the standard Karmic setup (no custom */etc/X11/xorg.conf*), which works fine.

---

### Post by MikeDK on 2010-01-11
how about the suspend, on lid close, does that work in karmic? im running lucid x86_64

---

### Post by Ace_NoOne on 2010-01-11
> **MikeDK said:**
> how about the suspend, on lid close, does that work in karmic? im running lucid x86_64
I don't rarely use suspend, but it does work here.
Closing the lid just blanks the screen for me (that's how I set it up IIRC).

---

### Post by MikeDK on 2010-04-16
are any of you having issues on using the latest intel driver from xorg-edgers on lucid.

im beginning to see issues on booting to normal screenresolution on the HP 2510p wich is 1280x800
i use the Driver     "intel"  option in xorg.xonf to, or else ubuntu chooses to use fbdev by default.

---

