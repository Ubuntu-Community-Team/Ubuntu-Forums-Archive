---
title: "Wireless won't work after upgrade to 10.04"
date: 2010-05-15
forum: General Help
---

### Post by flood222 on 2010-05-15
I am having problems getting my wireless to work after upgrading from 9.10 to 10.04. I believe this is a driver issue as when I do a lsusb listing it shows up: 
 
D-Link Corp. [hex] DWL-G120 Spinnaker 802.11b
 
however an ifconfig does not show any wireless cards. Only the eth1 and lo listings. 
 
This lists my card as working with ndiswrapper, however I've had no luck. 
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=D-Link_DWL-G120_Rev_B1](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=D-Link_DWL-G120_Rev_B1) 
 
Anyone have any suggestions? I am new to Ubuntu / Linux and really want to get this working again. 9.10 had no issues. Is it possible to revert back?

---

### Post by Leinarcane on 2010-05-15
You can Reinstall 9.10, but can't downgrade.

Thats a  USB wireless doggle correct? Have you tried any other USB devices to make sure your USB is working, there is apparently a bug in 10.4 with some USB doggles not working, mostly USB mobile broadband devices. It's mentioned in the Sticky **Known Lucid Lynx issues/bugs with workarounds **here:[B] [B][http://ubuntuforums.org/showthread.php?t=146947](http://ubuntuforums.org/showthread.php?t=146947)

[/B][/B]Try this and see if it starts :
```
ifconfig wlan0 up
```It may not be starting automatically.

Are you sure the driver is loading? Or have the correct driver?
```
lsmod
```Will show you all currently loaded kernel modules.

---

### Post by flood222 on 2010-05-15
Thanks for the reply! 
 
It is a usb dongle. 
 
I tried *ifconfig wlan0 up* and it gave reply *wlan0 ERROR while getting interface flags: No such device*
 
I know the USB is working, It works with other devices and when I do *lsusb*, the dongle is listed. *D-Link Corp. [hex] DWL-G120 Spinnaker 802.11b*
 
I dont think the driver is loading. I did lsmod, but am not sure what module I should be seeing?

---

### Post by Sin@Sin-Sacrifice on 2010-05-15
Re-install the driver?

---

### Post by flood222 on 2010-05-15
> **Sin@Sin-Sacrifice said:**
> Re-install the driver?
 
Now this is where I go total n00b.  How do I do that?  
 
I still have a 9.10 machine up and running, and the wireless works fine on it.  So I do have a good resource to look at for a working verson.

---

### Post by Sin@Sin-Sacrifice on 2010-05-15
Actually try to unload and load the modules first and see what that does. Research what module your card uses and replace b43 with it.```
sudo modprobe -r b43
``` ```
sudo modprobe -r ssb
``` ```
sudo modprobe b43
``` ```
sudo modprobe ssb
```

---

### Post by Leinarcane on 2010-05-15
I found a tutorial  that may help you, if Sin@Sin-Sacrifice advice dose not work for you. It's for  Debian, but is Ubuntu based Debian.
_[http://wiki.debian.org/prism54#p54usb](http://wiki.debian.org/prism54#p54usb)_
```
p54usb
```Is the kernel module, according to the _[Linux Kernel Driver DataBase]("http://cateee.net/lkddb/")_.

Here's a few links to help you with linux, they may not be the best out there but they seem ok.
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)
[http://linuxreviews.org/beginner/](http://linuxreviews.org/beginner/)
[http://ubuntuclips.org/](http://ubuntuclips.org/)
[http://www.ubuntu.com/training/e-learning/desktop](http://www.ubuntu.com/training/e-learning/desktop)
[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224)

---

### Post by flood222 on 2010-05-15
Thanks guys, I'll read thru/try the things suggested and report back.

---

### Post by flood222 on 2010-05-16
Thanks guys!  I got it working with your help!

When I did dmesg it showed there was a problem loading the drivers.  

Downloaded:
[http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.1.0.arm.0](http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.1.0.arm.0)
in "/lib/firmware" and renamed it to "isl3886usb"

Plugged it in and it worked fine.  

The more I use and learn Linux the more I like it. :KS

---

