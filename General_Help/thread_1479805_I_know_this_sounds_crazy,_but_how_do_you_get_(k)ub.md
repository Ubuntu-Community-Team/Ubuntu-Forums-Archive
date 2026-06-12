---
title: "I know this sounds crazy, but how do you get (k)ubuntu as fast as Vista?"
date: 2010-05-11
forum: General Help
---

### Post by vaiocomputer on 2010-05-11
After finetuning Vista (CCleaner, Advanced Systemcare, Revo Uninstalling excessive programs, startup and Windows services editing, avoid EVER using IE, cutting down excessive Chrome disk cache, avoiding Safari, as well as a few minor tweaks here and there) I have found it to quite zippy.  Even surprisingly so, since it rivals if not beats my ubuntu w/ KDE installed partition at smoothness and speed for many things, like file manager. Dolphin and Nautilus, especially Dolphin, load up files surprisingly slowly compared to Vista.

I have an Intel Core 2 Penryn T8300, 3 GB DDR2, and 160 GB devoted to Vista, w/ 34 GB free, 10.8 GB for ubuntu root w 4.4 GB free, 13.7 GB for Home partition w/ 4.5 GB free.

---

### Post by ngrieb on 2010-05-11
lol. I believe your problem is KDE.

---

### Post by vaiocomputer on 2010-05-11
I don't think I'm happy with that option. KDE is very interesting.

---

### Post by ronnielsen1 on 2010-05-11
>  160 GB devoted to Vista, w/ 34 GB free, 10 GB for ubuntu root w/ over 3 GB free
Personally, I'd have reversed that. 

Why I quit using kde after 4 years, it's a resource hog. If it's any consolation, your kde won't slow down in 6 months while your Vista will.

---

### Post by vaiocomputer on 2010-05-11
> **ronnielsen1 said:**
> 
Why I quit using kde after 4 years, it's a resource hog. If it's any consolation, your kde won't slow down in 6 months while your Vista will.

I doubt that.  I've had this computer for a year and half already, and I have the tools to get rid of the creeping bloat.  And since KDE 4 is undergoing extensive development, it's really interesting to try the 'state-of-the-art' in linux desktop experiences, although Dolphin and KDE in general feels kinda slow.  I want to try to tweak it faster, kinda like how I did with Vista.

---

### Post by cascade9 on 2010-05-11
> **vaiocomputer said:**
> After finetuning Vista (CCleaner, Advanced Systemcare, Revo Uninstalling excessive programs, startup and Windows services editing, avoid EVER using IE, cutting down excessive Chrome disk cache, avoiding Safari, as well as a few minor tweaks here and there) I have found it to quite zippy. 

Try 'vlite'. Should let you strip out a lot of unneeded junk from vista (and win7). 

> **vaiocomputer said:**
> 
I have an Intel Core 2 Penryn T8300, 3 GB DDR2, and 160 GB devoted to Vista, w/ 34 GB free, 10 GB for ubuntu root w/ over 3 GB free, 13 GB for Home partition w/ 4 GB free.

FYI- the closer to the start of the drive a partition is, the faster is it. Having the 1st 160GB for vista puts the /root, /home and swap partition on the slower end of the disc. That could well be impacting on your speeds. 

Anyway, if you really want a faster KDE with ubuntu, go for a minimal install, then install xorg, kde-minimal and kdm from the command line. Should be a lot faster than kubuntu-desktop. I havent actually tried this with kubuntu, that is going from my expereince with xubuntu/minimal xfce and some of thwe other distros I've used KDE4.x on.

---

### Post by ronnielsen1 on 2010-05-11
The easiest and safest way to free up memory in any Linux system is to stop unnecessary programs and background processes from running, and then get your system to remember how you like it.  [http://www.lifehacker.com.au/2007/12/slim_down_and_speed_up_linux/](http://www.lifehacker.com.au/2007/12/slim_down_and_speed_up_linux/)  Memory usage of Gnome and KDE depend on what theme you are using and applications you are running. You can slim down either one by choosing a non-textured simple theme and remove the worst performing applications. Use programs like top and xrestop to find out which programs are the worst offenders.  [http://ubuntuforums.org/showthread.php?t=32439](http://ubuntuforums.org/showthread.php?t=32439)

---

