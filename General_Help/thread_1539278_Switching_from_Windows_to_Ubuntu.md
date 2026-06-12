---
title: "Switching from Windows to Ubuntu"
date: 2010-07-26
forum: General Help
---

### Post by rpeasley on 2010-07-26
Hi,
I have been using Windows for almost 20 years and really would like to try something new.  My biggest hindrance is that I use a windows based program for my job (worship presentation software).  Powerpoint or openoffice equivalent programs are insufficient because they do not have scripture and customizable song database integration.  
A couple questions:
Can I use my windows programs on Ubuntu? (the main program is SongShowPlus 7.0)
Do I have to uninstall Windows in order to test out Ubuntu?

---

### Post by RiceMonster on 2010-07-26
> **rpeasley said:**
> Hi,Can I use my windows programs on Ubuntu? (the main program is SongShowPlus 7.0)

No. There is wine that can run *some* Windows programs, but it is defnitely not guarenteed to work. However, there may be an alternative for your program. What does SongShowPlus do?

> **rpeasley said:**
> Do I have to uninstall Windows in order to test out Ubuntu?

Nope. There's a few ways to try it out without erasing Windows. The quickest way is to boot the Ubuntu cd and select the first option which lets you try Ubuntu without affecting your hard drive.

---

### Post by Zorgoth on 2010-07-26
I would 

a) try Ubuntu on the Live CD to test hardware compatibility
b) try Ubuntu with wubi or VirtualBox to test whether wine will run your software.  It may not work, although if it doesn't there are many tricks to get around that you may want to try.
c) In your wubi or virtualBox install, check the Ubuntu repositories for any possible equivalent software; if there is, try it out; you would be *amazed* at the things I have found in there (although as a math/science/programming person there is a larger community supporting my kind of software).

Is this the software you are talking about?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5868](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5868)

It looks like the latest version may be poorly supported as it is rated bronze, but does work; you probably should it that yourself; often I have found that things rated bronze or even garbage can be made to work very well with minor tweaks.  Also, those test results are old and likely support has improved between 1.1.33 and 1.2 (at least 30 or so upgrades since then of wine) The 2007 and 2008 versions should work almost (or entirely) perfectly.

---

### Post by Zorgoth on 2010-07-26
If you want to do a full test of Ubuntu, you can also dual-boot; this would however require shrinking your windows partition and may make your system less stable; Windows will probably not break, but Windows may very well repeatedly break your Ubuntu in that configuration.

---

### Post by zack8food on 2010-07-26
if I would dual boot so that you can Ubuntu and windows on the same computer and when you start up you just choose which operating system to use

---

### Post by snowpine on 2010-07-26
Welcome to the forums, and good for you for wanting to give Ubuntu a try. :)

The best advice I can give is to set up a "dual boot" situation where Windows and Ubuntu are side by side, so you can choose which one you want to use each time you boot the computer.

ps You might want to visit the [Ubuntu Christian Edition forum]("http://ubuntuforums.org/forumdisplay.php?f=168") to see if anyone can shed some light on your SongShowPlus question.

---

### Post by Zorgoth on 2010-07-26
OK sorry it looks like I probably got he wrong software; I cannot find a thing for SongShowPlus on winehq.  To test it, you would have to install Ubuntu through wubi or VirtualBox.  If at first it doesn't work don't despair.  There are many, many ways to make things work.  Ask on the forums of either Ubuntu or wine if you have any problems.

---

### Post by Goolie on 2010-07-26
LiveCD for the win.  

Wine has had some very remarkable results when I used it.  I never thought I'd be using the StarCraft 2 beta on my ubuntu install.  

=P

There is a site with a list of Windows apps and their Linux equivalents.  I didn't bookmark it, but I know someone has it!

---

### Post by VH-BIL on 2010-07-26
WINE is a compatibility layer for Linux. It has a large database that shows how usable software in WINE at (appdb.winehq.org). You may find SongShowPlus in there but if you don't you can try it in WINE and enter an entry into the database for others.

You can try using VirtualBox which can create an actual instance of Windows running inside Linux. I use this sometimes to get Visual Studio which only runs in Windows running for my job. This should work for you if WINE does not.

You may be able to find a Linux software alternative as I am moving all my work from Visual Studio (Windows) to Mono-Develop (Linux)

---

### Post by corncob on 2010-07-26
I haven't had problems resizing windows partitions but you could also install Ubuntu to an external drive.

---

### Post by Zorgoth on 2010-07-26
NOTE: If you install it to an external hard drive, you MUST CLICK THE "advanced..." button on the installer at the last prompt and set the master boot record to be installed on the external hard driver (which will have a name like /dev/sdb).  If you did not manually specify very specifically that you are installing the bootloader on the external hard drive, even if you install the operating system entirely on that, it will use the MBR on your primary hard driver and it won't work.  It is fixable and won't kill data, but very, very annoying if you do this wrong.  I would not recommend that a new linux user installs Ubuntu on an external hard drive.

---

### Post by corncob on 2010-07-26
I had installed Ubuntu on an external HD (sdb) by mistake.  The drive was connected and Ubuntu decided to install itself there.  The bootloader installed to the internal drive (sda) by default but I had no problems.  It wasn't what I wanted to do and Ubuntu ran a little slower than expected through the USB cable so I eventually disconnect the external drive and installed it on the internal one along side of Vista.

One time I put a second internal HD into a computer.  I disconnected the first one (Windows) while I installed Ubuntu.  I then chose which drive to boot from in bios setup.  I guess this was equivalent to putting the bootloader on sdb.  It worked out fine.

---

### Post by corncob on 2010-07-26
Oh, okay.  I see why you'd want to install the boot loader on the external HD: [http://ubuntuforums.org/showthread.php?t=1539171](http://ubuntuforums.org/showthread.php?t=1539171)
I never did try to disconnect mine and then try to run windows.

---

