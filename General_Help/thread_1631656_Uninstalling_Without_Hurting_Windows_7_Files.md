---
title: "Uninstalling Without Hurting Windows 7 Files"
date: 2010-11-26
forum: General Help
---

### Post by Downloaded7 on 2010-11-26
Hey all,

I just got a new laptop for school work and I've loaded Ubuntu onto it without issue.  Now I'd like to free up some space on my desktop to use it primarily as a gaming computer.  I had Windows 7 installed long before I installed Ubuntu and I figured that uninstalling Ubuntu would be as simple as just deleting the hard drive partition but I can't see the partition in My Computer like I thought I would and when I googled how to do it I kept hearing people talk about Grub, which I have completely no understanding of.  I just want to delete Ubuntu without harming the programs I have installed on my Windows partition and so far the advice I've found online just doesn't make much sense to me.  Sorry for being so helpless, but if someone could give me a hand, that would be great!

---

### Post by wilee-nilee on 2010-11-26
Did you dual boot as in install Ubuntu from a booted cd, or did you install from a live Windows setup?

---

### Post by napoleon3665 on 2010-11-26
if you installed ubuntu from the live cd inside windows, all you have to do is put in a live cd and click the uninstall button and you're done. 

if you installed it from the live cd by itself and not inside windows, then all u need to do is boot into windows, delete the partition and extend it, and then fix the bootloader. 

take a look at this, its a pretty easy tutorial on how to do this. if u get stuck, just post here and ill help.

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

---

### Post by planetofdeviants on 2010-11-27
> **Downloaded7 said:**
> Hey all,

I just got a new laptop for school work and I've loaded Ubuntu onto it without issue.  Now I'd like to free up some space on my desktop to use it primarily as a gaming computer.  I had Windows 7 installed long before I installed Ubuntu and I figured that uninstalling Ubuntu would be as simple as just deleting the hard drive partition but I can't see the partition in My Computer like I thought I would and when I googled how to do it I kept hearing people talk about Grub, which I have completely no understanding of.  I just want to delete Ubuntu without harming the programs I have installed on my Windows partition and so far the advice I've found online just doesn't make much sense to me.  Sorry for being so helpless, but if someone could give me a hand, that would be great!

This could very ugly if you blindly trust in online tutorials and solutions.  A sure way to not harm your files is to back them up on some other drive.  Wipe the drive and reinstall windows.  Then put them back on.  It' may be more time consuming, but it's fail safe. Plus you start with a clean slate which is always nice.

---

### Post by The Cog on 2010-11-27
Since you say there is an Ubuntu partition, I assume you did a normal dual-boot install rather than WUBI. This means that when you boot, you get a GRUB boot menu offering you a choice of linux, linux recovery, windows etc.

If I'm right, then the first thing to do is to put the windows bootloader back on. I've never done that, but this might help: [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Once it boots straight into windows, you can safely remove the Linux partitions. The windows disk manager should let you do this. If not, fire up the Ubuntu live CD, choose to try without installing and run System->Administration->gparted partition editor to do it.

---

### Post by infowars on 2010-11-28
Hey,
Im learning what not to do here as what to do. I know if you can boot W7 use EasyBDC freeware to repair your MBR from Grub back to W7. 
About 3 clicks and bingo booting to W7 with no other OS ...

Follow all the other fantastic help to rid of un-needed partitions, and other suggestions and you are go to go!

ixquick.com search EasyBCD.

Hope that helps....

---

