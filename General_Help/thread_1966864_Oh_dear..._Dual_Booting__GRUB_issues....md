---
title: "Oh dear... Dual Booting / GRUB issues..."
date: 2012-04-27
forum: General Help
---

### Post by LFX64 on 2012-04-27
Quick history. I've used Windows, for years. I've tried Linux/Ubuntu a  few times. Once I think, when it was in version 7 or 8, once in 9, once  in 10. Didn't like it, not to mention compatibility was iffy with my  hardware. Skoot forward and I'm using Windows 7. Have been since Oct  2009. I liked it, but it grew boring and doesn't play nice with USB 3.0  and I've noticed over the years the sheer amount lacking within it, an  obvious setup to create a market for the next OS. 

For the past  4-6 weeks I'd been using Ubuntu 11.10 before moving onto 12.04 beta 2  and final beta. They ran well on my Dell XPS L702X laptop. Miles better  with Intel and Nvidia than my old AMD/ATI PC did before. Anyhow, I  wanted to start fresh because I was waiting patiently for 12.04 LTS  Official Release. I was using 12.04 LTS final before beforehand as a  test and the changes there from 11.10 were beautiful. 6-7 hours battery  with basic work on my XPS L702X is brilliant. So anyway, to the problem:

I  made the mistake of deleting the partition for Ubuntu in Windows using  EASEUS Partition Master. When I exited Windows, an tried to boot the  next day I got an error. GRUB rescue, etc. I immediately knew what I'd  done wrong. I reinstalled Ubuntu via USB, as I normally do and as was to  be expected, it gave me back the boot loader and I could pick Windows.  Good? Nope. When I set up 12.04 LTS, I was getting errors when trying to  install software. It'd then ask me to insert a Ubuntu CD. I went to  repositories or something like that and removed the duplicates, yet it  was still asking for a CD for only certain software. I even had trouble  installing the Synaptic Package Manager. Some installiations would fail  for apparently no reason, an things like Skype, which would run on 12.04  final beta reasonably well compared to now, didn't on the Official  Ubuntu 12.04 LTS OS.

I removed it again from Windows, since  that's the only way I know how. Still after getting tons of errors annd  annoyances it still won't play nice. Sometimes I got unknown filesystem  at start up, so I'd reinstall it again. I'd rather not deal with an  installation which isn't going well, I'd rather it work well from the  off, as it should do... right?

At the moment it works, but I want  to get rid of it, uninstall IT, and GRUB, giving me the boot loader for  Windows, so I know in future  how the hell to get rid of Linux without  it interfering with my OS selection. I need Windows 7 because I play  games on it, but I want to use Ubuntu 12.04 LTS because to be quite  frank, it's better than Windows 7, an looks nicer. Plus, another reason I  ditched Windows is because I'm pissed they're releasing Windows 8, when  it should in fact be a Service Pack for W7. Damn those silly fools or  poor souls who are merely going to buy the same re-branded OS with a  lick of paint. Such a greedy company.

Anyhow. In the GRUB loader.  Now I have Linux, an I also have "other versions of Linux".  Basically... all I want is everything sorted. I want one Linux and it's  recovery option in the boot loader. The memory tests and the Windows 7. I  want nothing else in there. It's bugging me because there are things  there, that shouldn't be and that is usually for a reason. Also, I want  to install this so I don't get stupid errors when running Ubuntu. It's  not behaving anything like it did on 12.04 Final Beta.

Windows 7 is pre-loaded so I cannot use the CD to get to the Windows boot loader thingy.

Oh  also, when I did install Ubuntu each time.. selecting "Erase and  reinstall Ubuntu alongisde windows 7". At the end of the long tedious  setup, it'd say error: could not install boot loader. This is a FATAL  ERROR. I think I managed to get past that once, but 99% of the time,  whether I pick /dev/sda, 1, 2, 3, etc, or /dev/sdb it'll fail, claiming  it cannot go there and that it is a Fatal Error. Rebooting sometimes  brings me back to the GRUB screen allowing me to pick Windows 7 or Linux  (I'm on Windows 7 typing this) but sometimes it won't. What I mean by  that is, if I succeed in reaching the boot loader, it is okay from then  on, but if I don't, I'll always get errors. However either way, Ubuntu  isn't behaving well at all an I want to sort the MBR and/or GRUB out. I  also want to know how to get rid of Ubuntu and GRUB without messing  about, whereby it says erorr: GRUB RESCUE when I try to boot to Windows,  because obviously GRUB does something to the MBR giving you that nasty  purple crap at the start. lol 

Really appreciate the help give.  These past 4-6 weeks have been a joy on Ubuntu, but these past 2 days  have been a nightmare. Please help me fix this.

Thanks



Basically,  I want all Ubuntu stuff, GRUB, everything, all removed, an if possible,  whatever Ubuntu did to the MBR. Then I want to freshly install it  alongside Windows 7, as I have done in the past, without errors with the  boot loader. Hopefully elleviating problems when I update packages,  etc.

I have a Core i5-2540m 2.6Ghz, an I installed the amd64 one. I have 6GB of RAM, I want to use it :)

Sorry for the essay.

Peace

---

### Post by oldfred on 2012-04-27
Do you have Windows repairCD or USB?

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you prefer a gui, this program works well on repairing many issues.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
or
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I like to have several repair tools in my tool box as well as the repairCDs or USB  or liveCDs for every system installed.

If you have Ubuntu installed, you can post bootinfoscript so we can review it. Also what video card as often grub2 boots but then it needs boot parameters to get video card to work. Also with i5 you may have UEFI or BIOS as boot method, if you do not know you probably are booting in legacy BIOS mode.

---

### Post by LFX64 on 2012-04-27
> **oldfred said:**
> Do you have Windows repairCD or USB?

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you prefer a gui, this program works well on repairing many issues.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
or
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I like to have several repair tools in my tool box as well as the repairCDs or USB  or liveCDs for every system installed.

If you have Ubuntu installed, you can post bootinfoscript so we can review it. Also what video card as often grub2 boots but then it needs boot parameters to get video card to work. Also with i5 you may have UEFI or BIOS as boot method, if you do not know you probably are booting in legacy BIOS mode.

No I do not have a recovery disc for Windows. I have a recovery partition but I don't want it to mess with anything on my system. 

Why is removing Ubuntu and GRUB so damn difficult for regular users?

I just want Ubuntu, GONE. GRUB, GONE GONE. All traces of Linux, GONE. Windows to boot as it should. Reinstall Ubuntu 12.04 LTS, hopefully without issues this time. An have GRUB return to show just Linux, recovery, mem tests 1 and 2, an Windows 7, and then from there, everything just work.

So far it's been a complete and utter disaster. Which would you recommend trying first?

---

### Post by oldfred on 2012-04-27
You can use Boot-Repair to restore a Windows type boot loader to the MBR. Then make the Windows repairCDs or flash drives.

You can use gparted to remove the existing Linux partitions if you do not want to reuse them. If you want exactly the same partitions you can use manual install and just choose /, /home and it should find an existing swap.

Use Windows partition tools to resize Windows if need be, but not to add partitions or delete the Linux partitions as it does not correctly see them and sometimes writes a defective partition table.

---

### Post by LFX64 on 2012-04-27
I'm on Ubuntu at the moment running Boot-Repair but it runs infinitely and when I reboot (after giving up), it changes nothing. I'm running it again but it's been at it for the best part of half an hour.

Why do I need repair discs or need to create one? I don't want to. All I want is:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4

I want the extended partition on SDA4, as it was before all of this mess. Nice clean GRUB screen, an I want to know how to remove Ubuntu and GRUB, without any issues booting into Windows. I don't want to have to rely on silly repair discs, because GRUB is flawed. Yes, flawed. It alters the MBR, an when it disappears it leaves you stranded, unless you have... apparently, a Windows OS disc or repair media.

I want my GRUB screen clean as well. I know it's being picking but I dislike extra irrelevant boot options, which are the remnants of a previous buggered up installation. Multiple of which were caused by Ubuntu 12.04 LTS behaving NOTHING like 12.04 Final Beta did.

Rgh... this boot-repair seems to be doing absolutely nothing.

Surely there is a way of repairing the MBR, an removing crap out of it?

I never use Windows Partitioner. I always easeUS. I don't trust Windows.

---

### Post by oldfred on 2012-04-27
If you are in Ubuntu and just want a Windows boot loader. You will not be able to boot Ubuntu after this except the liveCD.

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.


You can remove old kernels so they do not show in the grub menu, just be sure not to remove the one you are using, with new versions you may have to install synaptic or just use grub customizer:

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI (or CLI)
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

When you break something is it good to have a repair disk. But if you have good backups then reinstall is ok.

---

### Post by LFX64 on 2012-04-27
Back to MBR. I managed to sort it and boot into Windows, which was hardly the problem in the first, so now I'm going to re-download the 64bit Ubuntu ISO and delete Ubuntu through Windows using easeUS. Then I'll re-run the Live USB.

Annoying thing happened though. It appears my System Reserved Space with Dell Utility on it, is appearing under (V: ) drive letter in accessable drives on Windows. So I have this one. OS (C: ) and Local Disk (V: ).

I'll mess about with it and see if it keeps coming up.

This is mega annoying. I may just swipe the entire drive and install Ubuntu if this keeps messing me about.

---

### Post by LFX64 on 2012-04-27
I removed the drive letter. Sorted. Now Windows doesn't read it. Annoyance solved.

I've deleted Ubuntu partitions and the MBR is sorted.

Now I'll put the fresh Ubuntu ISO on the USB with the updated Universal USB Installer thing. Fingers crossed.

---

### Post by oldfred on 2012-04-27
I prefer to use gparted to manually create partitions and then use manual install to format partitions and choose which is / (root) and swap is usually found. With manual install you can then also create a separate /home. Partitioning in advance also lets you create another NTFS partition for shared data. It is ok to read from Windows system partition but Windows sometimes does not like too many writes. So a shared works better.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:

Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by LFX64 on 2012-04-28
I just typed a paragraph explaining my fixes and other problems, an it magically cleared itself.

Anyway. Boot issues no longer a problem. I have a cycle I use to sort that.

Other issues:

Duplicate sources, every time. I uncheck them in apt-get / software updater.

Super slow updater. Packages about 5MB in size take forever to download, yet downloading through Firefox gives me 1.1 ~ 1.3MB/s downloads.

Installing some programs asks me to use the CD/DVD Ubuntu 12.04 LTS Precise Pangolin disc. This is a common problem and I've had it every time I've installed this. It claims it needs it to install packages that some software is dependent on.

The installation process is flawed. Also, a common failing area for updates when installing the system and updating is nvidia related stuff. I have switchable graphics. An Intel Core i5-2540m 2.6Ghz Processor with Intel HD 3000 IGP and a seperate dedicated Nvidia GT-550m 1GB DDR3 VRAM Video Card. This was never a problem before.

Ubuntu is undoubtly my favourite operating system, but this is massively different now. For some reason 11.10 suffers the same hangs on installation whereby it didn't before, and it's the same with 12.04 in that it asks for a disc. Sources are properly selected in Software Updater.

I want to stick with one functional OS and I'm quite used to Ubuntu to a certain extent, a lot more than I have been in the past where I only tolerated/tried it for a few days. But this is more hassle than it is worth. Something changed, an it's effecting my ability to install programs and the thing which asks for a disc is very annoying.

I'm tempted to try Linux Mint, although this tedious, delete partition / restore MBR / install OS business, is frustrating me.

What the hell is going on? What is going wrong? :(

Note: I have a Dell XPS L702X and I always run 64-bit OSs. ](*,)

Edit: Many apps crash too. One common crash victim being the Ubuntu Software Centre.

---

### Post by LFX64 on 2012-04-28
Tried everything. Disaster.

Tried Debian but their website is massively confusing, an their net installer sucks a big donkey schlong.

Then I tried Linux Mint, which I'd considered before. It was initially my second choice, an I regret not picking it as my first OS way back. No Unity. Nicer looking interface. Works straight out of the box with practically everything. Gnome. Java, Flash, MP3 etc. Skype installed instantly, no issues whatsoever. An the good size icons at the top are nicely designed. Overall. massively impressed.

Ubuntu 12.04 lost me.

I'll be sticking with Linux Mint 12. Badass.

Thanks for suggesting boot-repair by the way... very useful.

Lee

---

### Post by oldfred on 2012-04-28
Downloads may be slow because everyone is downloading new version. Have you updated to use a more local mirror?

[http://ubuntuforums.org/showthread.php?t=1967019](http://ubuntuforums.org/showthread.php?t=1967019)


I think you have to decide which video you want. The nVidia should give a lot more performance. Do you not specify in BIOS whether to use internal or external video?

From update manager, settings button, Ubuntu software tab - do you have CD checked? uncheck if you do.

---

