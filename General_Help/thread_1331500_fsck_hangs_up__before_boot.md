---
title: "fsck hangs up  before boot"
date: 2009-11-19
forum: General Help
---

### Post by relic70 on 2009-11-19
The normal fsck check before booting has hung up on two occasions in the last couple of days. Probably the first fsck checks since a fresh install.

My system: dual boot Dell Dimension 8300
first hard drive - sda - Windows XP
second hard drive - sdb - Ubuntu 9.10, separate /home partition

The second hard drive was a new larger drive to replace the original smaller drive. I did a fresh install of 9.10 on that drive.

after the fsck hang up, both times, I did a Ctrl-Alt-Delete to kill the process and boot.

The fsck message is as follows during the second fsck check

fsck from util-linux-ng 2.16

dev/sdb1 : clean xx/xx files xx/xx blocks
dev/sdb5 : clean xx/xx files xx/xx blocks (check in 4 mounts)
modem-manager: Loaded Plugin: Huawei
modem-manager: Loaden Plugin: Option High-Speed

(there were about 10 of these and then)

modem-manager (tty S1) opening serial device .....

And this is where it hung up for almost one hour before I stopped fsck

Nothing like this ever happened in previous versions - 9.04, etc.

Anyone else have this happen?

Any input to solve this problem would be greatly appreciated.

---

### Post by valeryc on 2009-11-19
I've got exactly the same problem on Dell Mini9 with ext2 filesystem. Every time it does fsck on boot it hang after some modem messages (as described above).

---

### Post by relic70 on 2009-11-29
I find it difficult to believe that nobody besides myself and valeryc don't have a problem like this with fsck!

---

### Post by mikodo on 2009-11-30
> **relic70 said:**
> The normal fsck check before booting has hung up on two occasions in the last couple of days. Probably the first fsck checks since a fresh install.

My system: dual boot Dell Dimension 8300
first hard drive - sda - Windows XP
second hard drive - sdb - Ubuntu 9.10, separate /home partition

The second hard drive was a new larger drive to replace the original smaller drive. I did a fresh install of 9.10 on that drive.

after the fsck hang up, both times, I did a Ctrl-Alt-Delete to kill the process and boot.

The fsck message is as follows during the second fsck check

fsck from util-linux-ng 2.16

dev/sdb1 : clean xx/xx files xx/xx blocks
dev/sdb5 : clean xx/xx files xx/xx blocks (check in 4 mounts)
modem-manager: Loaded Plugin: Huawei
modem-manager: Loaden Plugin: Option High-Speed

(there were about 10 of these and then)

modem-manager (tty S1) opening serial device .....

And this is where it hung up for almost one hour before I stopped fsck

Nothing like this ever happened in previous versions - 9.04, etc.

Anyone else have this happen?

Any input to solve this problem would be greatly appreciated.

I've started to get this on boot also. No ideas as to what is going on, never happened in 8.04 and have been using Karmic for a month now and it just started happening!

Any ideas?

---

### Post by relic70 on 2009-12-01
I posted the same problem on the Linux Questions forum and the responder there said it was not a problem with fsck but with the modem. Hence, the "tty s1" at the hangup. In my case, I have a PCI modem card. He suggested removing the card or if the modem is built in to disable it in the BIOS.

I'm going to remove the PCI card and see what happens.

---

### Post by BigMeanMikeRich on 2009-12-02
I've been having the same problem with Karmic.  Upgraded from 9.04 (which ran flawlessly since I installed it the day after release), had problems immediately with modem-manager hanging the system at boot.  The only fix that worked was to remove modem-manager with apt.

Now, a month later, every time I boot the system after a complete power-down, the system hangs at a message that reads 'fsck from util-linux-ng 2.16' Three things stand out:

1) The hard disk activity light is not on, indicating that fsck, if any was even being performed, is not active

2) I do *not* get messages about modem-manager like relic70, as I removed it earlier.

3) I do not have any modems, onboard or PCI.

Alt+Ctrl+Del reboots the system, which comes up fine.  The next time I turn the system on from a complete power-down, the fsck fiasco occurs again.

---

### Post by valeryc on 2009-12-02
I don't have a modem on my Dell Mini9 either. Also, if it's an issue with modem manager, why it only happens after fsck run and not on regular boots. I've manually decreased frequency of "on-boot" fsck runs and will wait for a solution for a month or so and if it doesn't come will install Win7 instead.

---

### Post by Dilutu on 2009-12-03
Same problem here and I dont have a modem either....Th

---

### Post by Dilutu on 2009-12-04
I removed "modem manager" and it booted 5 times ok so far.......Th

---

### Post by Zoot7 on 2009-12-04
If you're having problems with fsck on bootup, then boot off a live cd and run this:

```
sudo fsck -y /dev/sda1
```
Assuming /dev/sda1 is the partition where Ubuntu is installed, make sure to use the right one.

---

### Post by mikodo on 2009-12-04
My problem was more like described by BigMeanMikeRich. Having an external modem provided by my ISP; I unplugged it for 10 minutes and then plugged it and restarted my rig and have not had a problem with fsck hanging on boot since. May be totally unrelated, but for now I'm having no problems with fsck hanging. I'll have to wait and see I guess.

Just ran fsck through $ touch /forcefsck and no hanging either.

---

### Post by valeryc on 2009-12-05
It seems that the latest kernel update fixed the problem for me. I've ran a forced fsck on boot couple times and no more hangs. Hopefully, this is it for this bug.

---

### Post by jim_charlton on 2009-12-23
I guess this thread is getting old... but I have been having a similar problem on a 64bit machine running the latest release of karmic (2.6.31-16-generic).  It is fully updated and upgraded.  It started hanging once in a while during fsck of logical volumes (I am using lvm).  Lately, it has absolutely refused to boot at all. I have been tearing my hair out!  It will not boot to single user mode (recovery).  It will boot if I append "rw /bin/bash" to the kernel line in grub but then most of the system is not loaded (upstart/init has not run?).  I recently found that if I append "rw /sbin/init --debug" to the kernel line in grub, it will boot just fine!  I don't see the --debug option in the man page for init.  I found it on an older web page whose reference I have now lost.

Is this a problem with upstart? Or perhaps with one of my upstart jobs? Anybody have a clue?

---

### Post by LykkeLamaen on 2010-01-18
I have a similar problem and I'm completly unable to get into ubuntu.
I just installed ubuntu 9.10 on my toshiba portege m200 and it hung after the reboot when updating all the packages. 

I tried putting rw /bin/bash or rw /sbin/init --debug in the grub options but it doesn't seem to work. The messages are slightly different but the systems still hangs around this message

```
fsck from util-linux-ng 2.16
[  4.7015221] Adding 2441840k swap on /dev/sda5. Priotity:-1 extends:1 across: 2441840k
/dev/sda1: clean, 152745/3514368 files, 894200/14040002 blocks
```

I don't know what to do. I can't use a live cd to get into the system because my BIOS won't accept USB or CDs to boot from.

---

### Post by jomsa on 2010-01-22
Started to happen to me too after upgrade from 8.04 to 9.10 about a month or so ago. After lot of investigation it turns out that FSCK for some strange reason just freezes and mountall remains to wait it to finish up (which it will never do) and hence it wont mount it. Killing fsck (with a bit of gable ofcourse) and manual mounting of the disk, fixed the problem, but i suspect it will return on next automated fsck.

---

### Post by saewelo on 2010-01-23
I'm having exactly the same issue using the Ubunut netbook remix.  I disabled the boot splash and sure enough the autorun of the fsck hangs and never completes

---

### Post by saewelo on 2010-01-23
I'm having exactly the same issue using the Ubunut netbook remix.  I disabled the boot splash and sure enough the autorun of the fsck hangs and never completes

---

### Post by gstratton on 2010-01-26
I also seem to be seeing similar symptoms to at least some of the people in this thread.

I had a working Karmic machine (64-bit server, I think) which I attempted to reboot, and now I can't get it to boot at all.

On startup I see a couple of messages about fsck running on my RAID partitions, and a few messages regarding network interfaces pre and post start scripts, but nothing else. In particular there is nothing that seems to be running at the point the system hangs.

I've tried booting various kernels and their recovery modes; I've tried passing some of the suggested arguments to the kernel. The machine will boot fine from a CD. This problem is really unpleasant and it seems also quite obscure.

We'll keep trying to get this machine up, but any suggestions regarding what could have changed would be gratefully appreciated! Thankfully this is only a development server, but I hope our production servers don't get rebooted any time soon.

Regards,

Graham

---

### Post by gstratton on 2010-01-26
It seems like our problem was that someone had removed /etc/network and replaced it with a sym-link to a non-existent location. That would explain the messages about network scripts failing. Sorry for the noise.

---

### Post by octobuntu on 2010-02-17
I get the exact same error ona fresh cli install of karmic. It seems that after a run script to install a desktop from a ssh session, that error message appears upon reboot. I have tried several different window managers, and I have no modem installed. I do ahve the drive partitioned to ext4.

---

### Post by hatapota on 2010-02-18
Has anyone found a way around this problem yet? I can't get ubuntu to load at all and I'm getting so frustrated. I don't really know what I'm doing so have no idea what I could try, other than continually restarting the computer and crossing my fingers that it will work. In normal mode it just stops at the fsck, recovery mode has more text but (I think) essentially the same thing, and I can't boot from a cd so can't try that.

If anyone has any suggestions at all I would be so so grateful!

---

### Post by jesterthejedi on 2010-02-25
Use a live cd, boot into ubuntu, try without installing mode.

Next open the terminal and enter this in:
sudo fsck -f /dev/sda#

REPLACE # with the actual numeral. It will take a few minutes to scan and repair, but it will reset your start up count fro fsck.

---

### Post by hatapota on 2010-03-01
I've finally got this fixed - but not on my own. My brother is a debian developer and I eventually convinced him to come round and take a look at it. Synaptic package manager had been doing an update and it turns out that the update was interrupted by the computer restarting - I guess it must have thought it had finished the update. Lots and lots of totally incomprehensible (to me, anyway!) terminal stuff, and my computer is working properly again.

I have no idea what I would have done if I hadn't had someone I could call on to fix this though, it seems like quite some glitch.

---

### Post by RT236 on 2010-03-08
I had a somewhat similar problem on a new install.  I have 9.10 running on several desktop systems here, no problems... but, I have a Toshiba Tecra 8100 (older system I use for backup if desktop fails, nice laptop).  I did a fresh 9.10 install, went well, loaded all new updates, went well, then I did reboot, and then got the fsck hang and never got the boot splash login screen.

I tried the suggestions here, same problem.  I reloaded 9.10 again, same fsck hang on boot.  Could not really find much on this, checked Launchpad bugs, etc.

Here's what worked in my case at least for me.

I decided something must be roached in the boot sector.  I used "Darik's Boot And Nuke"  [http://www.dban.org/about](http://www.dban.org/about) and did a complete data destruction on my disk.  Then I reloaded 9.10 WITHOUT then doing updates, was able to boot OK many times. I then downloaded updates, but did not reboot from updates screen. I shut system down, then did restart to complete updates.  My system has worked perfectly since I did this.  In my case I think there was something residing on my disk that fsck did not like.

I have no idea exactly why this worked, I'm just relaying what worked for me.  I was really getting frustrated trying to get past the fsck hang and no boot splash login screen.  I've been running Ubuntu here for quite awhile and SuSE before that a long time.  I've not encountered this type of error before during boot.  It seems to just effect a few systems, I guess.

Hope this helps someone.  Fortunately I was doing a fresh install at the time.  If things change and my laptop starts hanging on fsck during boot again I'll update this...

UPDATE:  It's been about 4 days now and this fix for me has been working perfectly. Just an FYI.

---

### Post by dert on 2010-03-26
Hi guys, this is a HUGE problem.  I spent 2 days putting together a brand new i7 PC, complete with dual boot Ubuntu Studio 9.10 x64 and Windows 7 x64.  I had it just the way I liked it and it was working SA-WEET!  Until the updates came that is...then my brand new PC died with:

ubuntu 9.10 fsck from util-linux-ng 2.16

Nice, eh?  I googled all the fixes and there really aren't any ones that are easier for the uber-noob than a total re-do.  So even now I'm in the process of redoing the entire drive.  I'm light years beyond upset but I'm really happy this occurred NOW at the beginning rather than 2 months from now with lots and lots of data hanging around.

I filed launchpad bug 548601.  In the meantime, do NOT restart you PC mid-way through any updates.  That's what's doing it I believe.  :frown:

---

### Post by chellrose on 2010-04-04
> **jesterthejedi said:**
> Use a live cd, boot into ubuntu, try without installing mode.

Next open the terminal and enter this in:
sudo fsck -f /dev/sda#

REPLACE # with the actual numeral. It will take a few minutes to scan and repair, but it will reset your start up count fro fsck.

How does one find out what the sda# is for the Ubuntu partition on a multi-boot computer?  Grub gives me the numbers for Windows but not Ubuntu.  I've tried various other things with no success.

---

### Post by Peter K Nicol on 2010-04-05
When the fsck problem starts up you will be able to read the number off the end of the first line. My machine has this problem now and again. Today it has been 3 hours and it's still checking - now on line 2821.172544 (it stared around line 24. ?
Lines start with a number then 
ata 3.00 exception then 
ata 3.00 cmd 20/00:08... then 
ata 3.00 res 40... then 
ata 3.00 status {DRDY}.
Sometimes another two lines are added starting 
end request then
buffer I/O error
Can anyone explain what is going on and how to fix it. I would be really grateful and I am sure I wouldn't be the only one.

Peter

---

### Post by mariourk on 2010-04-20
I booted with the livecd and mounted the partition with my Ubuntu installation, simply by opening *locations* and selecting the right partition.

Then I opened a terminal and chrooted into my Ubuntu installation.
```

chroot /media/the-uid-of-your-ubuntu-partition/ /bin/bash

```
After that, I ran:
```

apt-get update

```
But this failed and started to complain about an interrupted dpkg. So I ran:
```

dpkg --configure -a

```
This spawned loads of errors about not having permission on some files (mostly /dev/null). But it did seem to fix something. Maybe mounting /dev, before chrooting, would have been a good idea. But it seemed to work anyway.

I rebooted my system. Instead of booting Ubuntu, I choose the recovery mode and did a check on any broken packages. From what I saw, it finished an interrupted update and installed loads of packages.

After that, I did a reboot and found my system working again!

I hope this will help someone.

---

### Post by UncleAlan on 2010-09-21
It seems when this problem occurs the only way out is to start again from scratch!
 
My pc doesnt seem to want to boot from the cd. I dont mind redoing everything but is there ANY way i can access the hard drive to back up some files?
 
Running 9.10 with the cd in from start i get the grub version 1 screen and the option of generic or recovery neither of which work. it just goes to some gibberish ending in blocks.
 
Surely there is a fix to regain access to the current hard drive.
 
Any one know how?
 
Alan

---

### Post by mariourk on 2010-09-21
Most likely your harddrive (and the data on it) is fine, since this is a software issue.

The easiest way of dealing with this, is to yank out the harddrive and replace it with a new one. Harddrives as so cheap these days... :biggrin:

Do a clean install on your new HDD without risking to loose any data. Once you have done that, you have 2 options:

1) You install your old HDD as a second HDD in your PC and copy your data from there to your new install.

2) You buy a [IDE/SATA-to-USB converter](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156102) (also not that expensive and very handy to have around anyway ;) ) and attach your old HDD to a USB port and copy the data to your new install.

---

