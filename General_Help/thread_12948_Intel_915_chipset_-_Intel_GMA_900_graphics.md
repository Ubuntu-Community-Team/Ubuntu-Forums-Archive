---
title: "Intel 915 chipset - Intel GMA 900 graphics"
date: 2005-01-27
forum: General Help
---

### Post by siroj on 2005-01-27
I' getting rather poor video performance on my new PC with integrated Intel GMA 900 graphics, video playback stutters and windows can't be dragged smoothly (they're followed by traces of the window's border).

I've been searching the internet for information on how to set up Linux/X for use with Intel GMA 900 graphics, but haven't really found anything usefull.

My questions:
- what drivers should I use?
- where do I get those?
- what should my configuration look like?

I'm also interested in other Intel 915 chipset-related hints or performance improvements. In formulating your answer, please consider the fact that I'm a recent switcher (new to Linux).

(Thanks in advance).

---

### Post by daniels on 2005-01-27
Full accelerated i915GM support has been integrated into Hoary, our development branch, which will be released in April.

---

### Post by siroj on 2005-01-27
I've already upgraded my Warty installation to Hoary. Does that mean I currently have the best video performance possible with this graphics card, or could it be there's something wrong with my configuration?

---

### Post by daniels on 2005-01-27
It should be the best performance possible, but there's always the chance that you've hit a bug ...

---

### Post by siroj on 2005-01-27
During the xserver-xorg setup I selected i810 as the 'desired x server driver', because there wasn't anything else that looked better among the options provided. Was this the correct choice?

After selecting i810, the setup seemed to autodetect my video hardware as "Intel Corporation i915 Integrated Graphics Controller"...

---

### Post by daniels on 2005-01-27
Yep, i810 is fine.  And you're running Hoary, you say?  If you could attach /etc/X11/xorg.conf and /var/log/Xorg.0.log, that'd be great.

---

### Post by siroj on 2005-01-27
I went through dpkg-reconfigure xserver-xorg a few times and somewhere along the way I must have broken something: maximum resolution I'm getting is 800x600 @ 53 Hz, re-running dpkg-reconfigure and enabling higher resolutions doesn't solve this...

---

### Post by siroj on 2005-01-27
I reverted back to the XF86Config-4 file that was still in the /etc/X11 directory, and now I've got my screen back at 1024x768, but that's using the vesa driver...

I'm sorry to waste your time because I'm touching files I don't completely understand, but does anyone know how to get my graphics back to work with the i810 driver? (manually changing the xorg.conf file to i810 doesn't work).

FYI: the monitor I'm using is a Dell 783p Color Monitor, the manual lists following specs:

Horizontal scan range 30-85kHz (automatic)
Vertical scan range 50-160 Hz (automatic)
Optimal preset resolution: 1024x768 at 85 Hz
Highest preset resolution: 1280x1024 at 75 Hz
Highest addressable resolution: 1600x1200 at 60 Hz ("Dell does not guarantee the image will be sized and centered correctly etc...")

My current xorg.conf file, actually a renamed XF86Config-4 file, is attached to this post.

---

### Post by davidrcuervo on 2006-04-08
Hello,

I had the same problem with the resolution, that is because you must enable the capacity of 1280x800. just follow the solution in the web page: 

[https://wiki.ubuntu.com/i915Driver](https://wiki.ubuntu.com/i915Driver)

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

### Post by ajack on 2006-05-15
I hope my post is not "out of topic" but with Dapper, your graphics chipset will be detected and installed correctly and a "glxinfo | grep direct" confirms that the graphics is hardware accelerated.

However, if you use a new install with the current dapper beta (flight7) build.  The screen will go blank when Xorg is doing the hardware detection and you will not be able to see the rest of the install process nor input any prompt after that until the installation is complete and the computer does a reboot.  Everything works fine after that though.

I have opened a bug report with Ubuntu at URL [https://launchpad.net/distros/ubuntu/+bug/44776](https://launchpad.net/distros/ubuntu/+bug/44776)

Hope this helps.  :mrgreen:

PS.  I also have a thread here discussing the problem at URL [http://ubuntuforums.org/showthread.php?t=176575](http://ubuntuforums.org/showthread.php?t=176575)

---

