---
title: "geforce 8600 gt... driver support broken"
date: 2009-09-09
forum: General Help
---

### Post by vwr0527 on 2009-09-09
hey ever since the move from 8.10 to 9.04 I couldn't use nvidia proprietary drivers anymore... After the usplash screen loading bar, the screen flashes black and text, then it's in some 800x600 mode saying 'oops! i broke'. I told it to make an archive of whatever problem was ailing it., here's an excerpt from it
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux microvac 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep  9 03:23:47 2009
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000046gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
NVIDIA: could not open the device file /dev/nvidia0 (Input/output error).
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:5:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

```

so theres Failed to initialize the GLX module;, then there's couldn't open device file /dev/nvidia0 (i checked, it's there)

in conclusion, after a fresh install, it correctly guessed the native resolution of 1440x900, then I updated it so it's completely up to date, then restarted, then i went to restricted hardware manager where I installed the 180 version of nvidia, and then restarted and then it broke.
Now I'm stuck at 800x600, using the default xorg.conf.

COMPUTER SPECS: Amd athlon 3000+, 1 gb ram, asus neo k8n platinum motherboard, a 8600 GT, and I recently installed a TV tuner card a few slots below it.

---

### Post by vwr0527 on 2009-09-09
not getting anymore views so bump

---

### Post by NoaHall on 2009-09-09
Right, first, remove any in use. Install again, then run "sudo dpkg-reconfigure xserver-xorg"

---

### Post by vwr0527 on 2009-09-09
gotcha, and this will get me my 1440x900 back, and restore the basic drivers

---

### Post by NoaHall on 2009-09-09
Yep.

---

### Post by vwr0527 on 2009-09-09
ok, now my xorg.conf looks like this
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
and I have both the nvidia-common and nvidia-glx-173 packages and their dependencies all installed, and my screen is normal again

EDIT: Also have implemented the workaround where you go to /etc/rc.local and added chmod 666 something

---

### Post by NoaHall on 2009-09-09
So it's all fixed? Or is there something else you want to fix?

---

### Post by vwr0527 on 2009-09-09
I would like to get my awesome graphics card to be working, so I can use google earth or compiz. I'm an eye candy man.

---

### Post by NoaHall on 2009-09-09
Just install from the "System-> Admin -> Hardware"
Then run the reconfigure again.

---

### Post by vwr0527 on 2009-09-09
Just to be sure, I tried again, and it did that same exact thing. :(
most recent log in /var/log/gdm/:1.log
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux microvac 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Sep  9 13:16:41 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000107gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
error setting MTRR (base = 0xf9000000, size = 0x00e00000, type = 1) Invalid argument (22)
```
and if I run the dpkg-reconfigure again, I'll get a default xorg.conf, so I wouldn't get 3d acceleration anyhow

---

### Post by NoaHall on 2009-09-09
try running "sudo ldconfig" and then try. And maybe if you can, change the // on /usr/lib/xorg/modules/extensions//libglx so it's /usr/lib/xorg/modules/extensions/libglx

---

### Post by vwr0527 on 2009-09-09
I'm pretty sure the extra backslash is normal, otherwise, how could it know that within //libglx.so: there is an undefined symbol: _nv000107gl?
it couldn't have invented that symbol name itself, so it must be able to look inside libglx.so, right?
besides I can't change it. My only hint is "dlopen" and I don't have a clue where it is.
Also, I sudo ldconfig'd right after installing the glx-180 drivers via the restricted hardware manager, and then restarted the computer, and it still said the same thing. I took a picture of what the exact words were, so here I recite them:
```
Ubuntu is running in low graphics mode
the following error was encountered. you may need to update your configuration to solve this.
(EE)Failed to load /usr/lib/xorg/modules/extentions//libglx.so
(EE)Failed to load module "glx" (loader failed, 7)
(EE)NVIDIA(0):Failed to initialize the GLX module;
```
The rest isn't interesting or informative, just the same ****.

OK, I looked in /usr/lib/xorg/modules/extentions/ and found libglx.so, apparently it's a Link to shared library (application/x-sharedlib) and it links to libglx.so.180.44 [note no path]
This is probably the same for every fresh ubuntu installation, just thought I might give it a shot and see if you all have something different.

---

### Post by vwr0527 on 2009-09-09
I just got a reply from the nvidia forums
[http://www.nvnews.net/vbulletin/showthread.php?p=2082332&posted=1#post2082332](http://www.nvnews.net/vbulletin/showthread.php?p=2082332&posted=1#post2082332)
and they say that
>  Originally Posted by AaronP  View Post
I thought I replied to this, but it seems my reply got lost... reposting.

This indicates that a conflicting version of libGLcore is installed somewhere. Since you installed the Ubuntu driver packages, you'll need to contact Ubuntu support to resolve this packaging error.
Hmm, I'm gonna uninstall libGLcore, see what happens...
EDIT: Can't find such a package on synaptic... not giving up yet

---

### Post by oldfred on 2009-09-09
I had some issues also. I have updated Ubuntu since 2006 and have about 30 backup xorg.conf files. I also recently converted from 7600gts to 9600gt Nvidia card.

I tried many things, but someone recommended uninstalling all nvidia drivers and cleanly installing the 180.xx driver. I some how created a vesa version of my xorg and booted that, housecleaned everything and then reinstalled and it works. I also created a new partition and installed the 64bit version of Ubuntu and it worked without any issues.

I have some of the double slash entries in my log file that works so that is not an issue. My xorg is 4.7 KB and has a lot lf modelines to define resolution like:
ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

---

### Post by Perfect Storm on 2009-09-10
Try this;
Disable the driver first in "Hardware Driver", then;

```
sudo apt-get remove --purge nvidia-common nvidia-glx-173 nvidia-glx-180 nvidia-settings nvidia-173-modaliases jockey-gtk nvidia-180-modaliases
sudo apt-get install jockey-gtk nvidia-glx-180 nvidia-settings nvidia-common nvidia-glx-173 nvidia-173-modaliases nvidia-180-modaliases
```

Go back and choose the nvidia driver v. 180

---

### Post by vwr0527 on 2009-09-10
> **Artificial Intelligence said:**
> Try this;
Disable the driver first in "Hardware Driver", then;

```
sudo apt-get remove --purge nvidia-common nvidia-glx-173 nvidia-glx-180 nvidia-settings nvidia-173-modaliases jockey-gtk nvidia-180-modaliases
sudo apt-get install jockey-gtk nvidia-glx-180 nvidia-settings nvidia-common nvidia-glx-173 nvidia-173-modaliases nvidia-180-modaliases
```

Go back and choose the nvidia driver v. 180

OK but from your second line I had to remove the "nvidia-glx-173" because you can't both have that and nvidia-glx-180. restarting...
...back.
Sorry this problem is so rotten.. It still doesn't work and it's still 
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000046gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)

that.
I was thinking about the nvidia tech's comment, that this was a conflict with another libGLcore. I quoted him earlier...

---

### Post by Perfect Storm on 2009-09-10
I'm not quite sure what the problem is. It happens that an upgrade goes really bad. If you have your /home on a separate partition it would be quicker re-installing a clean version.

---

### Post by vwr0527 on 2009-09-10
i would've... i would've. but it's just that this IS a fresh installation. I reinstalled it thinking that it was an update that went bad, but lo and behold, no. It's fresh out of the box and it's got ants in it. :l
Maybe it'll be fixed by 9.10, which should be soon.
As for now, well I guess the next step would be to file a bug report on bugzilla. I can still use the 'nv' drivers anyway

---

### Post by Perfect Storm on 2009-09-10
If you have the stomach, you could go with 9.10 development release.

---

### Post by urunewbuntu on 2009-09-13
I had almost the same problem, and I finally solved it with this
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

hope that help you!!

---

### Post by vwr0527 on 2009-09-15
I fixed the problem... Here's how. After scouring the internet for millenia, I found this
[http://forums.nvidia.com/index.php?showtopic=42278](http://forums.nvidia.com/index.php?showtopic=42278)
and then my NVIDIA forum guy Aaron points me to the obvious place, the readme.
[http://www.nvnews.net/vbulletin/showthread.php?p=2082332&posted=1#post2082332](http://www.nvnews.net/vbulletin/showthread.php?p=2082332&posted=1#post2082332)

and the readme: [http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-08.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-08.html)
RTFM RTFM
Anyway I added these to my kernel parameters acpi=off and vmalloc=128M
btw kernel parameters!? It's just adding the snippet right after your 'kernel' line in /boot/grub/menu.lst
took me a while to figure that out btw.

FRAKING IRQs

---

