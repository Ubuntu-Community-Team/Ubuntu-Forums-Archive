---
title: "Boot stalling at xubuntu splash screen help please"
date: 2012-08-02
forum: General Help
---

### Post by chipppy on 2012-08-02
Good evening

I have a xubuntu installation that is stalling at the xubuntu splash screen.  The bios all looks good.  The unit starts up after the POST=1 beep with nothing odd.  it gets the xubuntu splash screen and the progress bar moves to approx 30% and then it all frezzes there.
I lucked out and got a routine disk check, but that stalled aswell.  The progress bar moved across a little more this time and the word 'keys:' appeared at the bottom of the screeen.

Anyone got any ideas of what I can try to repair this box.

Cheers
chipppy

---

### Post by chipppy on 2012-08-06
bump

---

### Post by decrepit on 2012-08-06
I think there's a method for going into verbose boot mode. That may show where it's stalling. Can't remember how to do it, but a search may come up with something.

---

### Post by chipppy on 2012-10-03
Good Afternoon  

How do I achieve one of the following.
1.     Fix the currput 3.0.0.20 problem.
Get a copy of linux-header-3.0.0.20 and where do I replace it 

2.     Change my system so that it starts via the working 3.0.0.17 normally without any intervention.  
Currently starting via 3.0.0.20 and fails but can be manually selected to start from the 3.0.0.17 if I interven during the start proccess 

3.     Manually delete linux-header-3.0.0.20 so that I can complete and upgrade to 12.04

I am finally back for holidays and work trips, and back to fixing my Mythbunutu box

OK from the hints above I found [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

I loaded up via a Ubuntu 12.04 LiveCD and followed the instruction

Ran fist time and it wanted MD raid installed (my system is a 8TB RAID5 system that holds all the important stuff).  Did as it asked > [QUOTE]RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y --force-yes mdadm --no-install-recommends)[/QUOTE] and boot-repair was now happy.

Next problem was my system is also 64-bit (another popup)
> [QUOTE]64bits detected. Please use this software in a 64bits session. (Please use Ubuntu-Secure-Remix-64bits ([www.sourceforge.net/p/ubuntu-secured](www.sourceforge.net/p/ubuntu-secured)) which contains a 64bits-compatible version of this software.) This will enable this feature.[/QUOTE]

ran through the 64-bit LiveCD and all seemed to go we.  popup came about dmraid interfearing with MDraid.  I didnt really understand so I say 'no' to removing the packages
At the end said repaired with the following popup> Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1257573/](http://paste.ubuntu.com/1257573/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (2000GB) disk!

Rebooted computers and got to the 'select boot type' screen.  The one where there is normal boot, recovery boot, boot older linux version, etc.  I like the dual boot screen (but this is a linux only box)
I let this run through and same frezze occured at the splash screen.
Rebooted again and went into recovery mode.  I found nothing wrong via the various options.  Rebooted and frezze again.
Rebooted again into older linux version and all good.
After a lot of playing around I have finally worked out the following
My Linux-headers-3.0.0.20 is corrupt somehow.

> 
Package in inconsistent state

The package 'linux-headers-3.0.0-20' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.


I am assuming that no archive can be found due to it being an older version and nolonger supported.  (Yes I do have an older system.  If it isnt broken dont fix it).  I did try a fully upgrade but this error prevent me from doing the upgrade.

SO
How do I achieve one of the following.
1.     Fix the currpot 3.0.0.20 problem.
Get a copy of linux-header-3.0.0.20 and where do I replace it 

2.     Change my system so that it starts via the working 3.0.0.17 normally without any intervention.  
Currently starting via 3.0.0.20 and fails but can be manually selected to start from the 3.0.0.17 if I interven during the start proccess 

3.     Manually delete linux-header-3.0.0.20 so that I can complete and upgrade to 12.04

Greatly appreciate any help

Cheers
Chipppy

---

### Post by chipppy on 2012-10-07
bump

---

