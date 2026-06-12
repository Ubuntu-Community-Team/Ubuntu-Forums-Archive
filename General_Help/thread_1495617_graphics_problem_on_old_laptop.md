---
title: "graphics problem on old laptop"
date: 2010-05-28
forum: General Help
---

### Post by kadafi69 on 2010-05-28
I got round to installing 10.04 on an old fujitsu siemens alimo em laptop.

when I boot up I am greeted with this error:

> The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernal module.
Please check your
(EE) NVIDIA:    system's kernal log for additional error messages.
(EE) Failed to load module "nvidia"(module-specfic error, 0)
(EE) No drivers available.

So I have to boot up in low-graphics mode, when I use the hardware drivers to search for graphics drivers, none turn up.

any ideas?

---

### Post by DagMan on 2010-05-29
If you have nvidia drivers installed try running this to see what's there of nvidia
```
dpkg --get-selections|grep nvidia|grep -v deinstall
```
you can then go about 
```
sudo apt-get remove --purge PACKAGENAME
```
you pretty much just want to get rid of the drivers, for example I have a box that has intel drivers but it still has the following when I run the dpkg command above.
nvidia-173-modaliases				
nvidia-96-modaliases				
nvidia-common					
nvidia-current-modaliases
So these are part of the Ubuntu install.  I doubt removing them would be bad on my machine though since I don't have nvidia and I tend to think that on a system with nvidia drivers that resinstalling repo drivers would bring them back in, but I'm not sure about it.

Also, on most newer Linux, for quite a while now, you can usually use open source drivers by moving your xorg.conf file and rebooting, so 
```
cd /etc/X11
sudo mv xorg.conf xorg-conf-old
```
and if it causes a problem you can always move it back.

If you get things to where they're acceptable to view the screen, then perhaps you can move forward with getting the drivers on there.  I'm unclear about just how old of a card the repo drivers support, though I'd think that even if the card was not supported that nvidia would have a driver to download that compiles itself.

---

### Post by kadafi69 on 2010-06-04
thanks for the help. I tried what you suggested but to avail. Ive tried searching for the drivers but couldnt find the right ones, so after a bit more investigating I found that the graphics is the SiS M650 chipset. So im at a loss as how to get this working.

---

### Post by DagMan on 2010-06-04
It may be that there isn't a great driver for those graphics in linux.
[http://forums.linuxmint.com/viewtopic.php?f=49&t=33872&p=195460&hilit=SIS+M650](http://forums.linuxmint.com/viewtopic.php?f=49&t=33872&p=195460&hilit=SIS+M650)
If all else fails you might want to invest in an old card that fits your box and does work, as suggested in the link.

---

