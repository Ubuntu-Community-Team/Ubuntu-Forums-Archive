---
title: "Failed to parse existing X config file"
date: 2010-04-05
forum: General Help
---

### Post by pretear on 2010-04-05
When I try to save my X configuration file.. it says "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

I've already deleted my current xorg.conf and created a new one using **sudo nvidia-xconfig** and run NVIDIA X server settings using **gksudo nvidia-settings** but still can't save..
I am using 32-bit Ubuntu 9.10 and my video card is NVIDIA FX 5500..

TIA : D

---

### Post by me13221 on 2010-04-05
post your xorg.conf file here so we can look at it.

---

### Post by byStanderone on 2010-04-05
...just a wild guess, perhaps nvidia is not allowed to alter native files, a manual edit of xorg.conf is the workaround...and the nvidia settings will follow suit.

---

### Post by vajras on 2010-04-11
i have the identcal error message  - and i cannot post my org.config file because it empty!

I am trying to change my dual screen setup but it oly remains until i reboot/logoff/restart etc - then do it all again!

Any ideas would be welcome, pls?

---

### Post by Linuxforall on 2010-04-11
In terminal gksudo nvidia-xconfig, this will create a xorg.conf file. Then for resolution settings gksudo nvidia-settings 

Set your resolution and save the x file.

---

### Post by vajras on 2010-04-11
Thanks, so far so good.

---

### Post by Darkhorse85 on 2010-04-28
I have the same problem but this doesn't solve it! 

I ran the two lines of code as above (i read it in many other posts to and it was resolved) and when i change the resolution to the setting i want and save the error repeats.

Here is my xorg.conf after I entered the code


Section "Screen"
	Identifier	"Configured Screen Device"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

There is also the following error (along with failed to parse existing X config file) in the terminal when I press "save to x configuration":

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device"

---

### Post by wojox on 2010-04-28
That's weird try it again:

```
sudo nvidia-xconfig
```

---

### Post by Darkhorse85 on 2010-04-28
I just did this to the xorg.conf file, saw something on a mint thread and it worked:

Section "Screen"
Identifier	"Configured Screen Device"
DefaultDepth	24
EndSection

Section "Device"
Identifier	"Configured Video Device"
Driver	"nvidia"
EndSection


**CHANGED TO:**

**#**Section "Screen"
**#**Identifier	"Configured Screen Device"
**#**DefaultDepth	24
**#**EndSection

Section "Device"
Identifier	"Configured Video Device"
Driver	"nvidia"
EndSection

and it worked

---

### Post by Darkhorse85 on 2010-04-28
Thanx for the help wojox, nice page by the way.

---

### Post by pretear on 2010-05-01
I already managed to solve my problem maybe 3 weeks ago.. I just forgot to post my solution here.. LoL
anyway..
since I cannot save my X configuration.. I just manually edited the xorg file and put my desired resolution..

```


Section "Screen"
    Identifier    "Screen0"
    Option "metamodes" "CRT: 1024x768_60 +0+0"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection


```

---

