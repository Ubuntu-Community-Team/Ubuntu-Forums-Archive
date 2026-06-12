---
title: "Help: Ubuntu noob needs help"
date: 2009-09-14
forum: General Help
---

### Post by mechgamer123 on 2009-09-14
Hi everyone, I just installed ubuntu on a flash drive using a tutorial using pendrivelunix.com's tutorial, and I am having some problems. 
First. I have an 8800gt, and I cannot install video drivers for it to enable any visual effects, which is really disappointing. I go into the hardware devices app and "install" the latest version of the drivers, and it says I need to reboot, so I do, and it still says the driver is uninstalled. (I really want to use the cool fx in ubuntu!)
Second, My sound blaster x-fi xtremegamer is not producing any sonund, nor can I figure out how to use my sound card. Do I need drivers? Is there any support in v.9.04 (Version i'm using)?
Third, and this is minor, I have been trying to click the install button, but it says there is a partition that is in use, and it asks me if I want to try to stop the partition. I am asking if I can even install the full version of ubuntu on an 8gb flash drive. (Do I even need to?)
Thanks in advance

---

### Post by mechgamer123 on 2009-09-14
bump

---

### Post by P4man on 2009-09-14
> **mechgamer123 said:**
> Hi everyone, I just installed ubuntu on a flash drive using a tutorial using pendrivelunix.com's tutorial, and I am having some problems. 
First. I have an 8800gt, and I cannot install video drivers for it to enable any visual effects, which is really disappointing. I go into the hardware devices app and "install" the latest version of the drivers, and it says I need to reboot, so I do, and it still says the driver is uninstalled. (I really want to use the cool fx in ubuntu!)
Second, My sound blaster x-fi xtremegamer is not producing any sonund, nor can I figure out how to use my sound card. Do I need drivers? Is there any support in v.9.04 (Version i'm using)?
Third, and this is minor, I have been trying to click the install button, but it says there is a partition that is in use, and it asks me if I want to try to stop the partition. I am asking if I can even install the full version of ubuntu on an 8gb flash drive. (Do I even need to?)
Thanks in advance

You made a persistent live stick I assume? On such an install, adding drivers is not possible the regular way. It is doable, but if you are new to linux, this link (which explains how to add nvidia drivers to a live install, see item 14) will almost certainly overwhelm you:

[http://klik.atekon.de/wiki/index.php/CustomizeUbuntuLive](http://klik.atekon.de/wiki/index.php/CustomizeUbuntuLive)

An easier option is to do a regular install, the same way you would install to a harddisk, just to a USB stick. Bonus features include: much faster boot time, and no other livecd strangeness with configuration settings being reset and stuff. Big minus point: much more reading/writing to the stick, so it will wear out faster. Its not guaranteed to boot on any machine (especially not after installing binary video drivers) though it still works most of the time.

To do a regular install, you must boot a liveCD (or other stick) and then install on to the USB stick (or harddisk).

As for the X-fi.. I know there are issues with some of them, drivers being very immature still, but they do work for some ppl. It could be simple configuration issue (wrong output, muted slider), but perhaps we'll get in to that after you did a regular install..?

---

