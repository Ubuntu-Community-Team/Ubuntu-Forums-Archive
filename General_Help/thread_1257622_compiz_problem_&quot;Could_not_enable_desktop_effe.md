---
title: "compiz problem &quot;Could not enable desktop effects&quot;"
date: 2009-09-04
forum: General Help
---

### Post by imneal on 2009-09-04
Hello all, 

I can't get the Desktop Effects up and running.  I got the compiz-check script and ran it.  I was wondering if you guys might have any input:

Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 9800 GTX+ (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 


Any ideas?  

Thanks, 

neal

---

### Post by cocopuffz on 2009-09-04
What drivers are you running? The ones that came with Ubuntu or Proprietary drivers from nVidia? I run into problems using the drivers supplied by the community. Try installing the Proprietary drivers from nvidia. 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

It may even be the version of the drivers you're running causing problems. Try a rev older... I installed the newest version for my 9600gt one time and it performed crappy compared to the previous version. I skipped it, waited for the one after that and it worked great.

---

### Post by P4man on 2009-09-04
Are you running some other compositing engine by any chance ?

---

### Post by imneal on 2009-09-04
Yes, I am using the restricted drivers from ubuntu. I will try to install the nvidia and let you know.. Thanks!

I don't know what a composite engine is.  How can I find out?

---

### Post by P4man on 2009-09-04
a compositing engine, is a program that makes use of your videocard to draw effects like transparency, shadows, etc on your desktop. Compiz is one (the best known, and most powerful), but there are others like Xcompmgr, and even metacity.

If you don't remember enabling or installing any such program (eg, to run AWN dock or for screenlets?), then its probably not your problem. Still, to be sure you dont have metcity compositing on, run this in a terminal:
```

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

BTW, Id suggest sticking with the restricted drivers you have, and dont mess around with installing the drivers from nVidia site. While Im not sure what your problem is, the ubuntu restricted drivers (which are just packaged nvidia drivers) ought to work  just fine and should give you less headaches.

---

### Post by mc4man on 2009-09-04
> 
I don't know what a composite engine is. How can I find out? 
One thing that can occasionally happen is metacity can be set as the compositing manager. (and desktop effects can't then be set

To check that go in a terminal
```
gconf-editor
```
Expand 'apps' and go to metacity -> general

If the "compositing_manager" box is checked then uncheck it.

---

### Post by imneal on 2009-09-04
Thanks for all of your responses.  I am running Compiz as the composite manager.  I disabled metacity from the composite engine. 

I also tried to install the Nvidia drivers from the website :
NVISIA-Linux-x86-64-185.18.36-pkg2.run.  This just sent me to low graphics mode.  I had to restart xserver and reload the restricted driver for ubuntu.  

I guess I should give you some specs: 

Ubuntu 9.04 64bit.
Nvidia GeForce 9800 GTX+ (rev a2)
ASUS M3N78 Pro mother board (has GeForce 8300 onboard video)
8 gigs G-Skill DDR2 800 (should be 1066, but it doesn't run at that)
28" Hanns-G monitor running at 1900x1200
AMD Phenom quad-core

I just re-installed everything on this desktop yesterday, the restricted video driver seems to be running fine.  

The desktop effects worked fine when I was using onboard video.  But since I've upgraded and added a video card, it's not working. 

Thanks for any suggestions!

---

### Post by P4man on 2009-09-04
Hmmm.. thats odd.

I googled around a bit, and found someone with the exact same error as you with a comparable card:

[http://ubuntuforums.org/showpost.php?p=7156089&postcount=578](http://ubuntuforums.org/showpost.php?p=7156089&postcount=578)

A bit later he writes this:

>  <snip>

Following the comments there I discovered that when I did the upgrade from Intrepid to Jaunty the symlink at /usr/lib/xorg/modules/extensions/libglx.so got upgraded to the new file but the symlink at /usr/lib/xorg/modules/libglx.so still pointed to the old link.

I removed this link and recreated it to point to the new correct file /usr/lib/xorg/modules/extensions/libglx.so.185.18.04 and restarted the system, everything worked straight away.

Some people have said that the /usr/lib/xorg/modules/libglx.so symlink is not needed at all but I just recreated it.

I hope this helps someone. 

[http://ubuntuforums.org/showthread.php?t=799070&page=58](http://ubuntuforums.org/showthread.php?t=799070&page=58)

---

### Post by nbtrap on 2009-09-04
Delete your gnome configuration folder located at /home/<name>/.gnome2 then restart or log out and log back in. Your desktop will revert to how it looked when you first installed Ubuntu, but that can always be fixed.

---

### Post by nbtrap on 2009-09-04
Scratch that. You want to delete the folders /home/<name>/.gconf and /home/<name>/.gconfd if it exists. Sorry. After you do so and log out and back in, you should be able to enable the effects if your drivers are installed.

---

### Post by imneal on 2009-09-04
Thanks again for all of your responses.  Unfortunately, nothing has worked.  Here is what I have tried so far: 

turning off metacity as compositing engine.
install latest nvidia driver from nvidia.com (switched to low graphics mode).
deleting .gconf and .gconfd and loging out and in.
recreating link at /usr/modules/extensions/libglx.so so that it points to libglx.so.185.##### (I can't remember the number right now).

Alas,  When I try to enables extra effects, It searches for a driver (but never goes higher than 0%), changes to black and white a couple times, and then tells me that it could not enable the desktop effects.  

I'm about ready to try another nvidia driver, but that always leads to problems. If this doesn't work I'm going to reinstall everything.  Or maybe go over to 32bit mode, but that would just piss me off.  Any last ideas? 

Thanks again for all of your help!! you guys Rock!!!!

---

### Post by mc4man on 2009-09-04
> Any last ideas?
Myself not really, never had onboard video and never switched display adapters in an install.

The couple of times I had borked the drivers I usually had to go around in a couple of circles to get things back working

If you were thinking of a new install, you can usually test the restricted drivers from the live cd in jaunty before installing. 

All you need from the live cd is an internet connection and having restricted drivers available (should always be available for nvidia

To do so after the live cd loads abd internet is connected open System -> 
Admin.. Software Sources, enable all the sources on the Ubuntu Software page and disable the cdrom source. Then close and reload

Ater the sources list updates enable the restricted driver in system -> Admin..-> Hardware Drivers.

After it dl's and installs then don't restart, just log out and back in, the module will load. The message that you need to restart will remain but the driver will be loaded and advanced desktop effects can be enabled.

If from the live cd you don't get any restricted drivers avail. then maybe ck. your bios

---

### Post by P4man on 2009-09-05
last idea I got:
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by imneal on 2009-09-06
Well, I went ahead and changed over to Ubuntu 9.04 32 bit.  Everything works fine now.  I'm able to utilize my Nvidia 9800 card and set Desktop effects from all default settings and restricted drivers. 

thanks for all of your help and suggestions guys.  You're the people that keep me using Linux.  Else I would be tempted to just run back to Windows!!! 

So the solution:  ubuntu 64bit doesn't like the Nvidia 9800 GTX+ card, and until ubuntu upgrades those drivers, 32 bit is necessary.

Thanks again!!

---

