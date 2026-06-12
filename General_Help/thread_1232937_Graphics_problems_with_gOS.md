---
title: "Graphics problems with gOS"
date: 2009-08-06
forum: General Help
---

### Post by Omega234 on 2009-08-06
I guess this is the best place for this...

I recently acquired a new computer from my step-dad (old stuff from his office).  It's a completely solid state box (the case is its own heatsink), and as far as I'm concerned I cannot open the case.

I installed gOS (Debian variant, so similar to Ubuntu) on it (mostly because it only has 4.1 GB of space available).  It seems to have graphics troubles, though, as the highest resolution that actually fits my monitor is 1024x768.  All the outputs it lists are:

640x480
800x600
1024x768
1280x768
1280x800

Of course I want 1280x1024 (which my monitor handles, trust me), but it doesn't seem to output that right now.  I'm unsure of how to figure out what the graphics card is.  I'm not necessarily a Linux newbie - I've just never encountered this before (I'm not afraid of using the command line or anything).

Any help or suggestions would be greatly appreciated... thanks!

---

### Post by amitabhishek on 2009-08-06
What is your graphic card? Does it share ubuntu's repos? In fact I have also downloaded gOS but its not working under virtualBox...I don't know the reason...

---

### Post by 3rdalbum on 2009-08-06
The "lspci" command should tell you what graphics you have, and then from there we can help.

---

### Post by Omega234 on 2009-08-06
```
$ lspci
...
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
...

```
Those seem to be the only things related to graphics.

After a few searches, I've found [[COLOR="Blue"]this[/COLOR]]("http://intellinuxgraphics.org/2009Q2.html").  It would seem to be what I want, except I'm not sure if there might be an easier way to obtain the driver (i.e. without building it myself).

Thanks for the help so far!

---

### Post by Omega234 on 2009-08-10
So I've done a bit more reading and whatnot.  It seems that most people use the tool 915resolution to modify the screen's output.  Yet, of course, it didn't work.  I started with a fresh installation of gOS (after updating), and then did these:
```
$ sudo apt-get install 915resolution
$ sudo 915resolution -l
sudo 915resolution 58 1280 1024 32
sudo nano /etc/default/915resolution
exit
```

And /etc/default/915resolution is now:
```
#
# 915resolution default
#
# find free modes by /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size
MODE=58
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=1024
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
```

I've done all this, but still I can only display up to a square resolution of 1024x768.  Any suggestions?

---

