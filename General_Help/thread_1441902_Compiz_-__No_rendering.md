---
title: "Compiz -  No rendering"
date: 2010-03-29
forum: General Help
---

### Post by Dportner on 2010-03-29
So i recently upgraded to ubuntu 10.04 hoping that my graphics drivers were supported in there and i ran into some problems...

right now when i do compiz check i get:

```
Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

im really not sure how to fix this...

and also, my xorg.conf file seems very empty to other peoples xorg.files that iv seen in other threads
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
EndSection
```

---

### Post by Dportner on 2010-03-30
anybody have any idea on what to do???
come on people :(

---

### Post by Dportner on 2010-03-31
still nothing??
k maybe if i add some more information somebody will reply....

when i type "compiz" into terminal i get this

```
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```
everyonce in a while i would plug in my tv through a vga cord to my computer. is it possibly still looking for the extra screen?

please somebody help me.... its really frustrating not having compiz..

---

### Post by Dportner on 2010-04-05
ugh...come on people..

bump

---

### Post by toddwbucy on 2010-04-07
I am having the exact same problem.  Had no problems with 9.10 and compiz.  Once I upgrade to 10.04 though compiz failed.  Used compiz-check and got the exact same output as you.  I am running this on a IBM t60 with a ATI X1300.  here is my output fom the compiz --replace command in terminal:

:~$ compiz --replace
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
/home/redpill/.themes/[malys_GlaSS_NighT][02]/gtk-2.0/gtktreeview.rc:158: Unable to locate image file in pixmap_path: "Lines/line-h-tree.png"
/home/redpill/.themes/[malys_GlaSS_NighT][02]/gtk-2.0/gtktreeview.rc:161: Background image options specified without filename


any help with this one would be great.
Todd

---

### Post by lidex on 2010-04-07
Take a look at the lucid development forum:
[http://ubuntuforums.org/forumdisplay.php?f=377]("http://ubuntuforums.org/forumdisplay.php?f=377")

---

### Post by linden940 on 2010-04-07
10.04 is very new..there will be a few bugs..dont get to mad..they will all get worked out

---

### Post by chamrock on 2010-04-30
hi guys, i found the solution for me :
this is my default configuration for 32bit in /etc/X11/xorg.conf  :  

```

Section "Files"     
    ModulePath      "/usr/lib/xorg/modules"
EndSection
```



After upgrade to 10.04 , just add in section this:



```
 Section "Files"     
    ModulePath      "/usr/lib/nvidia-current"
    ModulePath      "/usr/lib/xorg/modules"
EndSection
```

It works!

---

### Post by imiunleashed on 2010-04-30
Got the same prob, got an ATI Card :(

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by straxus on 2010-04-30
Same problem on a 945GME.  "Rendering method: None".  With no xorg.conf file I don't know where to start.

---

### Post by lidex on 2010-04-30
Either an install or an upgrade generated an xorg.conf for me in the / folder. It's actually named xorg.conf.new 
Try this:
```
sudo updatedb
locate xorg.conf.new
```
If you do have one just rename to xorg.conf and move to /etc/X11/

---

### Post by straxus on 2010-04-30
No xorg.conf.new here.

---

### Post by lidex on 2010-05-01
Here are some links to check out:
Binary
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Open source
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

To create an initial xorg.conf:
```
sudo Xorg -configure
```

---

### Post by straxus on 2010-05-03
I found the solution in another thread.  It was:

1) Purge all nvidia related packages from the system.
2) sudo aptitude reinstall xserver-xorg-video-intel libgl1-mesa-dri xserver-xorg-core 
3) sudo dpkg-reconfigure xserver-xorg
4) sudo restart gdm

I skipped the first step initially, since this is a netbook that has never been configured to use nvidia drivers.  But after restarting GDM and enabling Compiz, all of the text and images were flipped vertically.  I stepped back through, this time purging the nvidia packages, and all was well.

---

### Post by puffead on 2010-05-04
what was this post that your talking about could you post a link

---

### Post by straxus on 2010-05-04
> **puffead said:**
> what was this post that your talking about could you post a link

[Certainly]("http://ubuntuforums.org/showpost.php?p=9212078&postcount=10").

---

