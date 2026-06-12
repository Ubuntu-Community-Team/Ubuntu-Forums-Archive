---
title: "Monitor Loses Signal During Live CD Boot"
date: 2011-09-27
forum: General Help
---

### Post by Juan Largo on 2011-09-27
I have the desktop i386 version of the Kubuntu 10.04.3 Live CD.  The md5sum of the burned disk matches the md5sum hash code published on the Kubuntu web site exactly, so I know the disk is 100% fine.  When I boot with the CD in the drive:

* I am presented a choice of languages, and I select English.
* I select the first option "Try Kubuntu without installing" on the boot menu.  (I don't select any other options.)

At this point, Kubuntu starts to boot and my monitor immediately goes to sleep.  If I manually power cycle the monitor, it says "No signal" and goes back to sleep.

I believe the Kubuntu Live CD continues to boot because there is a lot of disk activity on the CD drive.  When the disk activity stops, I still have a dead monitor with no signal.

I am using a stock HP Pavilion a1630n computer with an HP vs17e monitor.  There is nothing wrong with my CD drive.  I have tried at least 30 other Linux Live CDs on this machine, including Ubuntu, and have never had my monitor quit on me like this.  

I don't think it is a video driver issue because the monitor goes to sleep the instant the Live CD starts booting.  It is a complete loss of signal.  Should I try selecting another option from the Kubuntu Live CD boot menu?

When I run the Live CD in VirtualBox, it boots.  However, there is a lot of video "noise" on the monitor of the VM (multicolored hash) until I get to the log-in screen.

---

### Post by Juan Largo on 2011-09-27
I got the monitor to wake up by using a VGA=789 cheat code.

---

