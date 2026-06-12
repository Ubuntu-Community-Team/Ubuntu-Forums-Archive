---
title: "Ubuntu slows down my windows boot! WTF!!!"
date: 2009-11-14
forum: General Help
---

### Post by cycrosism on 2009-11-14
I installed ubuntu on my EEEPC (Using WuBi) and later on, I found out that ubuntu has no support for my usb tv tuner so I removed it because I wasn't just going to not use my 70 dollar TV tuner because ubuntu doesn't support it. I asked for help 3 times on this forum and didn't get an answer.

So anyway, after uninstalling ubuntu, it has slowed down my windows boot by HEAPS. The logo use to load really fast, now it loads at 1 frame a second, slowing down my boot by around 10-15 seconds.

I removed the ubuntu line in the windows boot loader, but it STILL loads really really slowly. I tried various different things and none worked. After each restart of my eeepc it still boots slower.

How can I fix this problem?

Oh and BTW, don't say it was my fault, Windows was working just fine before I installed ubuntu, now even after I removed it, it STILL loads slowly. I am using Windows XP at the moment.

---

### Post by cycrosism on 2009-11-14
Hi it's been 40 minutes, I am still wondering what I can do to fix this problem.

---

### Post by 311005901 on 2009-11-14
You may want to start over fresh and reformat the whole thing...

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
I really don't see how Ubuntu could affect Windows in that way. Have you installed anything in Windows recently? Also you might want to look into what Wubi did. I've never used it but it is a Windows application so it could affect Windows. If you ever want to dual boot again I would say do it from a Live CD. I've seen a few problems around here surrounding Wubi plus I've read a lot that says Microsoft is "out to get" Linux for their profit losses.

---

### Post by Benchamoneh on 2009-11-14
Just reformat your machine, but next time don't install Windows, put Wine on instead ;)

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
> **Benchamoneh said:**
> Just reformat your machine, but next time don't install Windows, put Wine on instead ;)

HAHAHAHAHAHAHAaaa... what about Playing Grand Theft Auto 4? Or Need For Speed anything? Or... well... that list can go on and on.

---

### Post by jeb800e on 2009-11-14
Download BleachBit for Windows. See if that helps... it should delete some unnessessary files, etc..

---

### Post by McMichael96 on 2009-11-14
Dude its Windows not Ubuntu! Just reformat you hard drive and then reinstall Windows (If it was me I would install Ubuntu instead of Windows but thats just me;))

---

### Post by cycrosism on 2009-11-14
Thanks for all the suggestions, but the thing is i do not have a CD drive on my eeepc (And it would cost 80 dollars to buy a usb one, so forget it) so I can't reinstall ubuntu, and it came with my eeepc so it might void the warranty if I remove it.

I will download BleachBit now and see if it solves the problem.

---

### Post by cycrosism on 2009-11-14
I ran a scan on basically everything and the problem is still here

---

### Post by jeb800e on 2009-11-14
Is there an Administrator version of Bleachbit that came with the Windows version? If so, try that.

---

### Post by cycrosism on 2009-11-14
I don't see any administrator version, only the 1 executable file it created. Oh and the uninstall file

---

### Post by Dullstar on 2009-11-14
When did you get your TV tuner?  If it was recently, it might not *yet* be supported.  By the way, I would like to know if you checked System -> Administration -> Hardware Drivers before you determined it wasn't compatible with Ubuntu (if you are using 9.10 it may not be exactly the same).

---

### Post by cycrosism on 2009-11-14
Well I removed ubuntu because it was slowing down my windows boot, but even after removing it, it is still slow. :/

---

### Post by Flying caveman on 2009-11-14
Change the time to display list of operating systems to 0 in your Windows start up and recovery options.  

If you installed Ubuntu with Wubi, just un-install it like you do any other Windows program, through the add/remove programs.  Is that how you "un-installed" Ubuntu or did you just remove the line from the windows boot.ini file?

---

### Post by wilee-nilee on 2009-11-14
You can find any residual Ubuntu files and wubi files by searching the hard drive from computer. I wonder if maybe you might have a infection. Here are two really good AV free programs that will run along any you have installed just choose the free versions and update them whenever you scan. I have used these to clean computer that McAfee said were clean. Also the Trojans...etc are set to disable the Major providers a lot of the time.

[http://www.superantispyware.com/download.html](http://www.superantispyware.com/download.html)

[http://www.malwarebytes.org/](http://www.malwarebytes.org/)

---

### Post by The-ITu on 2009-11-14
My gues, is that your ubuntu's partition is to big and takes up a lot of room on your hard drive. the less room you hard drive has, the slower it will go. maybe consider resizing your partitionto something smaller, or getting rid of ubuntu all together.

---

### Post by upapilot on 2009-11-15
Normally Ubuntu is on a completely different partition so it should not affect Windows in any way.....you probably must have installed a RAM hungry application on Windows recently which must have caused this increase in boot time

---

### Post by Giblet5 on 2009-11-15
You are going to be disappointed and frustrated until you do one of two things:


1. Track down the cause of your slow Windows boot. Windows provides tools for diagnosing boot problems, the easiest being the F8 key on your keyboard. Hit that during boot and select Boot Logging. You'll see what it's doing as it does it. So what's taking the longest?

There are third-party tools for diagnosing boot problems as well. Google knows all about most of them.

Try stopping some of the garbage from running at startup (quicktime, itunes, nero, transmitmycreditcardtonorway, etc).

Have you done *anything* to diagnose this problem, other than to point a finger at uninstalled Wubi on a Linux forum? Have you even looked at your Windows Event logs?


2. Go buy a USB DVD drive and reinstall Windows. You're going to have to do that eventually no matter how much you don't want to. That is Life With Windows...

Windows slows down. Everybody knows that. Yes, everybody. There are many reasons for it, some are semi-correctable, but the typical best fix is to reinstall or perform an upgrade/reinstall.

---

### Post by cycrosism on 2009-11-15
> **Flying caveman said:**
> Change the time to display list of operating systems to 0 in your Windows start up and recovery options.  

If you installed Ubuntu with Wubi, just un-install it like you do any other Windows program, through the add/remove programs.  Is that how you "un-installed" Ubuntu or did you just remove the line from the windows boot.ini file?

I have already changed the time to 0 seconds and I did uninstall wubi though the add/remove.

I have AVG free installed, no viruses were found.

Its no ram hungry application, it just takes longer for the windows XP logo to load, which takes 10 seconds. Normally it took 2-3 seconds so it has slowed down my boot time heaps just by having the logo take longer to load.

Also, this problem ONLY started after I installed ubuntu. Was never there before.

---

### Post by MaxIBoy on 2009-11-15
I've got to say, I'm dissappointed. There's a simple, obvious reason for this, and **no one** knows it!




Windows boots using [NTLDR](http://en.wikipedia.org/wiki/Ntloader) (windows NT LoaDeR) as a bootloader (Vista and later use something else which suffers the same exact problems, so we will speak of NTLDR and its successor as the same thing.) NTLDR is capable of loading Windows... and that's about it. It has no support for loading another OS.

In order to get Linux to boot, you need another bootloader. The most common one used with Linux is [GRUB](http://en.wikipedia.org/wiki/Grand_Unified_Bootloader) (GRand Unified Bootloader.) GRUB can load any OS which is compatible with the MultiBoot protocol. Linux is compatible, Windows is not. 

In fact, Windows can't really be loaded by anything besides NTLDR. Since Windows is closed source, we can't make GRUB work with it.

However, the Bootloader is called directly by the BIOS hardware of the motherboard, thus *all bootloaders must be called the same well-understood way.* So what we can do, is have GRUB "chainload" to NTLDR, and then NTLDR will do its thing and boot Windows. This is the only real way to dual boot Linux and Windows on the same hard drive.


So, installing Linux alongside Windows necessitates adding an extra step to the boot process. It used to be BIOS, then NTLDR, then Windows. Now its BIOS, then GRUB, then NTLDR, then Windows. That's just how it works. I'm afraid there's not much you can do about it if you want to dual-boot on the same hard drive.

If you would like to get rid of Linux and have your old Windows boot time back, use your recovery CD (which of course they don't give you anymore) or a Windows installer CD, and it will allow you to reinstall NTLDR to the Master Boot Record and remove GRUB.

---

### Post by Giblet5 on 2009-11-15
Edit2: > I've got to say, I'm dissappointed. There's a simple, obvious reason for this, and no one knows it!

This was a Wubi install. Your disappointment is misplaced. There's no grub MBR with Wubi...

---

### Post by jeb800e on 2009-11-15
> **McMichael96 said:**
> Dude its Windows not Ubuntu! Just reformat you hard drive and then reinstall Windows (If it was me I would install Ubuntu instead of Windows but thats just me;))
Bleachbit is available for Windows, as well as Linux

---

### Post by MaxIBoy on 2009-11-15
> **Giblet5 said:**
> Edit2: 

This was a Wubi install. Your disappointment is misplaced. There's no grub MBR with Wubi...
I know first hand that Wubi installs Grub and chainloads NTLDR... I guess I just kind of assumed that GRUB was being installed to the MBR. Sorry. But I was still more or less right...

---

### Post by Bjalf on 2009-11-15
System Restore?
Empty Recycle Bin?

---

### Post by MaxIBoy on 2009-11-15
Just thought of something else. Wubi sets aside a huge amount of space on your Windows NTFS partition. 

Try defragging it with [s]jkdefrag[/s] mydefrag (way better than the stock defragger.) [s][http://www.kessels.com/Jkdefrag/](http://www.kessels.com/Jkdefrag/)[/s] [http://www.mydefrag.com/](http://www.mydefrag.com/)

---

