---
title: "changing windows size takes forever"
date: 2010-05-02
forum: General Help
---

### Post by Mzwo on 2010-05-02
hi,

maximising, minimising or simply changing the size of a window takes ages and the whole system appears to freeze for a few seconds. system monitor registers a cpu load spike. 

a little annoying - what can be done?

please don't say "disable compiz", i need the cube ...

using a ati mobility radeon HD 2400.

thanks,
Matt

---

### Post by Mzwo on 2010-05-03
still slow ...

also, the pull down menus are a little slow to react and while there don't seem to be any performance problems while running programmes, starting and opening new windows is extremely sluggish. again, CPU load spikes. 

cheers,

Matt

---

### Post by Mzwo on 2010-05-03
ok, I've tried the following:

reinstall fglrx. no luck.
deactivate desktop effects. this only had the effect that I can't re-enable desktop effects. hmpf.
reinstall everything with compiz in its name. no luck.
remove fglrx. still sluggish.

I've got 4 GB of RAM, usage is hardly ever above 800 MB. 

am a little lost.

help appreciated.

Matt

---

### Post by fbkarsdorp on 2010-05-03
Hi, this a rather permanent problem with the propietary ati drivers. There are several workarounds, however. You could either try the no-backfill xserver, the back-clear patch or enable Direct2D.

Direct2D can be enabled with: 

sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE

and is described here: [http://www.webupd8.org/2010/04/how-t...ration-in.html](http://www.webupd8.org/2010/04/how-t...ration-in.html)

I personally prefer the backclear patch as I noticed that although the maximizing issue is reolved with Direct2D, scrolling in for example emacs becomes totally sluggish. You can find more information on the backclear patch here:

[http://www.phoronix.com/forums/showthread.php?p=125046](http://www.phoronix.com/forums/showthread.php?p=125046)

---

### Post by Mzwo on 2010-05-03
hi,

thanks. 
tried enabling direct2d and got the following:


> mzwo@mzwo-laptop:~$ sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
[sudo] password for mzwo: 
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.
mzwo@mzwo-laptop:~$ sudo aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections
mzwo@mzwo-laptop:~$ 


which means nothing to me. something is amiss, It'd appear.

Matt


edit: my xorg.conf reads as follows:



Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection



should i just add

Section "Layout"
EndSection


?

---

### Post by fbkarsdorp on 2010-05-03
you could try that, but an easier way is to:

1. backup your current xorg.conf

2. delete the contents of xorg.conf

3. let aticonfig make an initial configuration: sudo aticonfig --initial

4. then enable Direct2D: sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE

hope it helps.

edit: you probably have to log in and out to see the effect

---

### Post by Mzwo on 2010-05-03
did the patch thing instead, and it seems to work - thanks a million! was getting slightly frustrated ...

do I have to enable Direct2D as well, or would that be pointless?

Cheers,
Matt

---

### Post by fbkarsdorp on 2010-05-03
That would be pointless, I guess. The Direct2D is still in development, it works, but not too good... Enjoy your fancy desktop!

edit: please mark as solved.

---

### Post by Mzwo on 2010-05-03
...said and done.

thanks again.

Matt

---

