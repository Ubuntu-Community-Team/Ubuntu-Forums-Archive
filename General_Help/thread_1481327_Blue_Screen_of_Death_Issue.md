---
title: "Blue Screen of Death Issue"
date: 2010-05-12
forum: General Help
---

### Post by perfectpete216 on 2010-05-12
Hey everyone ! I am a new user here because I need help with this problem.

I am a Windows PC user, an HP G60-530US Notebook with Windows 7, and I repeatedly installed Ubuntu 9.10 and 10.04 LTS. You wonder why ? After installation and maybe about an hour of using Ubuntu, I reboot into Windows and I get Blue Screen of Death. I repeatedly had to reinstall Ubuntu and Windows, and I can't figure out if it's Ubuntu or something in Windows. I haven't got a Blue Screen in a few days, because on the 7th I installed 10.04 LTS but then removed it to prevent Blue Screens.

I have tried Wubi and the Live Disc installs, both with the same result in Windows!

I wanna know , is it Ubuntu? A bad file? Or is it Windows? Please help!

Specs: HP G60-530US Notebook
Windows 7
Pentium Dual Core T4300 at 2.10 GHz
3GB Kingston DDR2 RAM
320GB Hard Drive at 5400 RPM

---

### Post by perfectpete216 on 2010-05-12
Please help , I need it

---

### Post by snoopo71 on 2010-05-12
> **perfectpete216 said:**
> Hey everyone ! I am a new user here because I need help with this problem.

I am a Windows PC user, an HP G60-530US Notebook with Windows 7, and I repeatedly installed Ubuntu 9.10 and 10.04 LTS. You wonder why ? After installation and maybe about an hour of using Ubuntu, I reboot into Windows and I get Blue Screen of Death. I repeatedly had to reinstall Ubuntu and Windows, and I can't figure out if it's Ubuntu or something in Windows. I haven't got a Blue Screen in a few days, because on the 7th I installed 10.04 LTS but then removed it to prevent Blue Screens.

I have tried Wubi and the Live Disc installs, both with the same result in Windows!

I wanna know , is it Ubuntu? A bad file? Or is it Windows? Please help!

Specs: HP G60-530US Notebook
Windows 7
Pentium Dual Core T4300 at 2.10 GHz
3GB Kingston DDR2 RAM
320GB Hard Drive at 5400 RPM



What's written in your bluescreen?

---

### Post by perfectpete216 on 2010-05-12
Well, I don't remember, but most frequent is BAD_POOL_HEADER

---

### Post by no2498 on 2010-05-12
sounds like it may be getting hot

have seen a lot of ? for heat and not just laptops

---

### Post by perfectpete216 on 2010-05-12
In the hexidecimal code? No, but one I mostly see is 0x0000020 and usually the ones in parenthesis are filled with FFFFF

---

### Post by notbitmonk on 2010-05-12
I do not know what it is but I do not think that is heat.  perfectpete216 seems to be able to have W7 for a while without any heating problems.  Have you tried installing Ubuntu only (not shared with W7) and see if there is any trouble booting up, unexpected shutdowns, restarting?  If after a while is all good I would think that the problem is with W7 after the dual installation and would check the forums for dual installation/boot problem of W7 and 10.04.

---

### Post by perfectpete216 on 2010-05-12
Well the shut downs are only in Windows , Ubuntu works perfectly. I can't do that because if I delete my Windows, my parents would question and get mad, because I am a 13 year old computer genius. I would install it on a separate drive , but my BIOS can't boot from USB and it's only a laptop. I have considered trying a virtual machine, but I fear it will fail. Thank you for the advice though !

---

### Post by snoopo71 on 2010-05-12
I've been reading, probably you have a buggy hardware, let's try a memcheck:
winkey+r
cmd
mdsched.exe 
on reboot to the scanner press F1 for Advanced options and run the extended test.

Maybe you can find something.
But I don't realize, how ubuntu interferes with your windows drivers or hardware.

I don't know the answer of your problem I only tell you some resources to find something wrong.

---

### Post by perfectpete216 on 2010-05-12
I tried hard disk checks, RAM checks, and CD burner checks. No faults or flaws. I absolutely have no clue whats going on. I'm questioning if Microsoft programmed Windows 7 to find Ubuntu files as a threat to system intergrity.

---

### Post by elliotn on 2010-05-12
BSOD may mean faulty hardware, ubuntu wouldnt cause win7 to have a blue screen.

---

### Post by perfectpete216 on 2010-05-12
Thats the thing, my hardware is up to date and running perfectly.

---

### Post by perfectpete216 on 2010-05-12
I only have one other record of BSoD while running Windows alone, but I believe that was from overheating.

---

### Post by snoopo71 on 2010-05-12
Read this,[http://forums.tweaktown.com/f34/bad_pool_header-18119/](http://forums.tweaktown.com/f34/bad_pool_header-18119/)

---

### Post by perfectpete216 on 2010-05-12
This could be awhile..

---

### Post by perfectpete216 on 2010-05-12
I have to check every folder inside the drive? As in folder inside a folder ?

---

### Post by wilee-nilee on 2010-05-12
Post this bootscript, since you have done so many installs, we need to know some more pertinent information, post it in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Ubuntu would not cause a BSOD but user errors in installation can make things messed up. Also how did you resize W7 in order to dual boot? So please post the script and answer the questions.

---

### Post by perfectpete216 on 2010-05-12
I only did one Live Disk install, and I partitioned it from GParted , but it isn't Vista so I don't expect Recovery was over written. I usually installed with Wubi.

---

### Post by wilee-nilee on 2010-05-12
> **perfectpete216 said:**
> I only did one Live Disk install, and I partitioned it from GParted , but it isn't Vista so I don't expect Recovery was over written. I usually installed with Wubi.

And there is the problem your only supposed to use the W7 disk manager to resize the W7 partition. I would get the W7 disk recovery unless you have a install DVD and get to the recovery command line and run chkdsk /r. Here is a recovery disk link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Before doing anything though would you **_PLEASE_** post the boot script, if a error has occurred in where grub is, then the script will tell us this and other pertinent information. It is important to know whether you have a recovery partition, as well.

Your problem though I suspect is the partitioning it is a no no to use gparted to repartition W7.

---

### Post by spydeyrch on 2010-05-12
> **perfectpete216 said:**
> Well the shut downs are only in Windows , Ubuntu works perfectly. I can't do that because if I delete my Windows, my parents would question and get mad, because I am a 13 year old computer genius. I would install it on a separate drive , but my BIOS can't boot from USB and it's only a laptop. I have considered trying a virtual machine, but I fear it will fail. Thank you for the advice though !

When you say you can't boot from a USB, I am assuming that you are referring to installing to an external USB HDD, if possible, and then booting form that HDD.

Here is a link to make your PC bootable via USB even if your BIOS doesn't support it.

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

Perhaps you would then be able to just have Win7 on your laptop's HDD and if you wanted to, you could then boot from the external HDD into Ubuntu, just a thought.

I know that it doesn't solve your current issue but it may help in the fuutre. Plus, if you need/want to boot into a live pen drive, you can do it this way too and not have to waste a CD. :)

-Spydey:guitar:

---

### Post by bacardiandwatermelon on 2010-05-12
Just my two cents... Did you use the windows disk management to reduce the partition that windows uses? Sounds like you let the ubuntu installer to do it. I think if you run a repair on windows it should fix it for you.

---

### Post by wilee-nilee on 2010-05-12
> **spydeyrch said:**
> When you say you can't boot from a USB, I am assuming that you are referring to installing to an external USB HDD, if possible, and then booting form that HDD.

Here is a link to make your PC bootable via USB even if your BIOS doesn't support it.

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

Perhaps you would then be able to just have Win7 on your laptop's HDD and if you wanted to, you could then boot from the external HDD into Ubuntu, just a thought.

I know that it doesn't solve your current issue but it may help in the fuutre. Plus, if you need/want to boot into a live pen drive, you can do it this way too and not have to waste a CD. :)

-Spydey:guitar:

This is a excellent link but does not fix the bsod, which is probably due to using gparted to partition W7. Also with 7 installs grub could be anywhere.

We want to get W7 working again then we will get the dual boot worked out.

---

### Post by rueben on 2010-05-12
I have the same problem as well with my dual boot as well.It was due to overheating.Try shutting down from ubuntu and switch back on after 10 to 15 mins. It should do the trick.

---

### Post by wilee-nilee on 2010-05-12
> **rueben said:**
> i have the same problem as well with my dual boot as well.it was due to overheating.try shutting down from ubuntu and switch back on after 10 to 15 mins. It should do the trick.

fud!

---

### Post by no2498 on 2010-05-12
doing a lot of reading :popcorn:

---

### Post by rueben on 2010-05-12
> **wilee-nilee said:**
> fud!

fud?

---

### Post by 98cwitr on 2010-05-12
At what point does the BSOD occur?

---

### Post by wilee-nilee on 2010-05-12
fellow forum members please don't just post a idea without seeing the bootscript for one. Also W7 was shrunk with gparted that is not good and is the root of the problem, as well with 7 installs of Ubuntu we need to know about where grub is and information in general relating to the MBR. This is a user who does not need any junk information it does not help. ;)

---

### Post by spydeyrch on 2010-05-12
When you start up windows, do you at least get the windows loading screen? The little windows "flag" kid of "waving" in the wind.

If so, right before that comes up, can you hit F8 several times to see if you can get to safe mode?

This is what I am thinking, and correct me someone if I am wrong (as my wife typically shows me that I am, hehehehe  :P):

If in fact Grub wasn't able to load windows, in my experience, it would either show a blinking cursor in the upper right corner and just stay like that, or it would say something like "unable to boot, non system disk.....blah blah blah" when you selected windows from the boot menu (grub).

Just by the fact that you get the BSoD, tells me that windows is loading, at least to some degree, even if it is a minimal one. So, that would tell me that either it is an overheating issue, as previously mentioned by others, your disk has finally gone bad, or there is some kind of windows file configuration that is causing the BSoD.

If you can get into safe mode, perhaps we can troubleshot it from there. Then once we get it working correctly, we can get it dual booting properly.

Patience is something that you will need for this to work, sorry. :)

-Spydey :guitar:

---

### Post by spydeyrch on 2010-05-12
> **wilee-nilee said:**
> fellow forum members please don't just post a idea without seeing the bootscript for one. Also W7 was shrunk with gparted that is not good and is the root of the problem, as well with 7 installs of Ubuntu we need to know about where grub is and information in general relating to the MBR. This is a user who does not need any junk information it does not help. ;)

I don't see where the output of the boot script was posted. Did I skip it or look over it? :(
I saw the link to get it from sourceforge the but not the op's output of the boot script.

-Spydey :guitar:

---

### Post by Dayofswords on 2010-05-12
> **perfectpete216 said:**
> Well, I don't remember, but most frequent is BAD_POOL_HEADER
from the interwebz:

Question:

Windows stop BAD_POOL_HEADER error.
Cause:

This error is generated when a driver or part of Windows does not allocate the memory properly, and can be caused by any of the below possibilities.

   1. Bad hardware drivers.
   2. Issues with NTFS file system and/or disk write issues.
   3. Issue with software program, e.g. anti-virus scanner.

---

### Post by wilee-nilee on 2010-05-12
> **spydeyrch said:**
> When you start up windows, do you at least get the windows loading screen? The little windows "flag" kid of "waving" in the wind.

If so, right before that comes up, can you hit F8 several times to see if you can get to safe mode?

This is what I am thinking, and correct me someone if I am wrong (as my wife typically shows me that I am, hehehehe  :P):

If in fact Grub wasn't able to load windows, in my experience, it would either show a blinking cursor in the upper right corner and just stay like that, or it would say something like "unable to boot, non system disk.....blah blah blah" when you selected windows from the boot menu (grub).

Just by the fact that you get the BSoD, tells me that windows is loading, at least to some degree, even if it is a minimal one. So, that would tell me that either it is an overheating issue, as previously mentioned by others, your disk has finally gone bad, or there is some kind of windows file configuration that is causing the BSoD.

If you can get into safe mode, perhaps we can troubleshot it from there. Then once we get it working correctly, we can get it dual booting properly.

Patience is something that you will need for this to work, sorry. :)

-Spydey :guitar:

Right but do you know that partitioning W7 with gparted will cause this problem there is no auto chkdsk unless you run one. It is important not to speculate about grub when the bootscript will tell us exactly what is going on!

I suspect the OP is not on because he is using the chkdsk /r instead of posting the boot script, wanting a quick fix rather then following a standard protocol in these matters. If this is the case I hope it works, but I advised not to do anything until post the script.

---

### Post by spydeyrch on 2010-05-12
> **wilee-nilee said:**
> Right but do you know that partitioning W7 with gparted will cause this problem there is no auto chkdsk unless you run one. It is important not to speculate about grub when the bootscript will tell us exactly what is going on!

I suspect the OP is not on because he is using the chkdsk /r instead of posting the boot script, wanting a quick fix rather then following a standard protocol in these matters. If this is the case I hope it works, but I advised not to do anything until post the script.

So then in this case we would want the op to run the boot script, see how is HDD/Partitions/GRUB are setup and then proceed from there.

I was not aware of the fact that GParted doesn't work with Win7. I have used it multiple times with Vista and it worked fine, so I would have figured that it would work the same for Win7.

Without having to go over the entire thread again, has the op given us his specs? I know the boot script will tell us how the HDD/partitions/grub are setup, but what about general specs? I always like to start there personally. :)

-Spydey

EDIT: I did a little search online and found his machine's specs (hopefully I got the right one). Here thery are:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01860415&cc=us&lc=en&dlc=en&product=4041414](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01860415&cc=us&lc=en&dlc=en&product=4041414)

---

### Post by wilee-nilee on 2010-05-12
> **spydeyrch said:**
> So then in this case we would want the op to run the boot script, see how is HDD/Partitions/GRUB are setup and then proceed from there.

I was not aware of the fact that GParted doesn't work with Win7. I have used it multiple times with Vista and it worked fine, so I would have figured that it would work the same for Win7.

Without having to go over the entire thread again, has the op given us his specs? I know the boot script will tell us how the HDD/partitions/grub are setup, but what about general specs? I always like to start there personally. :)

-Spydey

EDIT: I did a little search online and found his machine's specs (hopefully I got the right one). Here thery are:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01860415&cc=us&lc=en&dlc=en&product=4041414](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01860415&cc=us&lc=en&dlc=en&product=4041414)

You are correct about the W7 partitioning. W7 has disk manager which is a virtual partitioner that will scan the disk and tell you exactly what can be done as far as shrinking it. Also a person wants to run a optimizer defragger 1st like the auslogics model, there are some that are even better but this one works fine. The control that the W7 partitioner has is pretty cool it is run on the live running OS.

---

### Post by perfectpete216 on 2010-05-13
Well I have given up on trying to dual boot. I am currently attempting a virtualbox install of Ubuntu, and with the BSoD it does get to the desktop, but then my computer crashes. Thanks guys for the help, wish me luck with the virtualbox! :D

---

### Post by perfectpete216 on 2010-05-13
I think I figured it out ! When I use Ubuntu , the wifi button flashes, I think it's my wifi card drivers !

---

### Post by perfectpete216 on 2010-05-15
I installed Ubuntu 10.04 LTS in Virtualbox - I had a problem with loading it up (I forgot to unmount the Install ISO) but now it's running inside Windows for a few hours now , no crashes no Blue Screens. :) I solved it

---

### Post by traderpats on 2010-08-10
Old thread but it come up in Google.  

Every time I tried Lucid via the live cd, upon returning to Windows 7 it would BSOD.  I tracked it down to the ati driver.  I had to go in Safe Mode and uninstall / reinstall the driver.  I've done it a few times so far trying to figure out a fix.  That's all I have...

---

