---
title: "Help regarding dual boot Ubuntu/WinXP with GRUB"
date: 2006-03-07
forum: General Help
---

### Post by fatmcb1 on 2006-03-07
First of all, I do regret that I am not greatly inclined technically with computers, and I appreciate anyones help.

I began several days ago attempting to dual boot WinXP Pro with Ubuntu. I'm running an athlon 64 with an 80gig SATA hard drive. Despite having an athlon 64 chip, I am attempting to run the standard version of Ubuntu (i believe i386) because they sent me a disc. 

After getting numerous errors, and partitioning all sorts of ways, I finally got it to work (BUT IT ONLY WORKED ONCE). I completely reformatted the hard drive after backing up all of my data. Then I made one FAT32 partition that took the entire hard-drive. I loaded the install cd and under the partitioning i chose the first option, which was to resize the primary partition. I did this in a manner that gave me an open 68 gb for windows (which I install later), and the remaining 12gb for Ubuntu. 

Everything from here goes great, and at this point I am able to finish installing everything regarding Ubuntu (including grub). Furthermore, I got Ubuntu fully functional as the only Operating System on the computer.

NOW, I went to install Windows XP Pro on the 68gb open partition. Everything went smoothly, and I am now typing on the Windows OS.

PROBLEM: As soon as I installed Windows, GRUB no longer works, and it automatically boots Windows, and I cannot get into Ubuntu, which I was so proud to get working.

I have attempted to do Google searches, and I can come across topics to restore GRUB, but they are just some lines of code that make no sense to a noob such as myself. If anyone could help me get GRUB working properly again so I can access both Operating Systems, I would appreciate it very much.

Thanks.

---

### Post by aysiu on 2006-03-07
You're supposed to install Windows first, then Ubuntu.

Windows will overwrite the MBR and not boot to Ubuntu.
Ubuntu can overwrite the MBR and will also boot to Windows.

The dual boot guide you're looking for is this one:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by BradChandler on 2006-03-07
It's usually best to install Windows first, then Linux when setting up a dual boot system. That way, the Linux bootloader is set up to allow you to boot into either OS. I think you have two options, either use the Windows bootloader or reinstall grub. Here's a link that describes setting up the Windows bootloader: [http://hacks.oreilly.com/pub/h/2337](http://hacks.oreilly.com/pub/h/2337)

If you post a copy of your boot.ini file from XP and a description of your hard drive partitioning, I could help you set that up. If you want to reinstall grub, here's a link that describes different methods of doing it: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

I'd recommend trying to reinstall grub, it probably makes things easier later.

---

### Post by ronmarley1 on 2006-03-07
Here's another really good dual-boot "How To"
[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

---

### Post by ComplexNumber on 2006-03-07
also, make sure that windows sits on the first part of the hard drive next to the MBR. if you install ubuntu first and put that at the beginning, then try to install windows so that it comes after ubuntu on the hard drive, windows will complain and just simply won't install.

---

### Post by fatmcb1 on 2006-03-07
Thanks for all of the help so far. Here is my predicament regarding installing Windows first: I had errors that I simply could not get around, and I used several guides, including the one listed by aysiu.

First I attempted to keep my Windows as it was, unformatted, and install ubuntu regularly using the 1st option in partitioner, which is to resize the partition. I tried this three times, each time getting errors. If it makes any difference, the partition I was resizing was NTFS.

After this failed I went ahead and reformatted the hard drive, Installed Windows, and tried it over again, except this time setting the partition tables myself. I attempted all sorts of combinations here, followed several guides, but regardless I got errors during the initial installation, usually debootstrap error.

This is why I decided to load Ubuntu first, figuring I could just set the entire partition to fat32, and then resize it using Ubuntu installer, install Ubuntu, and finally install Windows.

As my computer is setup now, Windows (the 68gig partition) is C: and Ubuntu (12gig partition) is D:

BradChandler: as soon as I get home from work tonight I'll post my boot.ini

Thanks again for the help.

---

### Post by aysiu on 2006-03-07
What errors did you get?

If I were you, I'd wipe your entire hard drive clean.

Install Windows. Defragment it.

Get ahold of a PCLinuxOS CD (as I've found [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) to be the most reliable partitioner) and resize the NTFS partition and create appropriate Ext3 ones, but don't install PCLinuxOS.

Install Ubuntu on the Ext3 partitions using the "Manuall edit partition table" option during installation.

---

### Post by Sutekh on 2006-03-07
If you are going to go to the trouble of re-installing Windows, don't install Windows on the full drive.  

You can use the Windows partitioner to create a partition that is as big as you want for Windwos, leaving the rest of the drive unpartitioned.  You won't need to resize the partition later when you install Ubuntu.

Some pics from this link

[http://www.resnet.uni.edu/docs/reformatxp.html]("http://www.resnet.uni.edu/docs/reformatxp.html")

 - Deleting any partitions

[IMG]http://www.resnet.uni.edu/docs/reformat/deletepartition.jpg[/IMG]

Creating partition by pressing C.  You will then be asked how big you want the partition to be.  The installer will probably offer the most space, but you can change it to what you want.  You will be left with unpartitioned space in which to put Ubuntu.

[IMG]http://www.resnet.uni.edu/docs/reformat/createpartition.jpg[/IMG] -

---

### Post by fatmcb1 on 2006-03-08
**It Works**

I followed the link that BradChandler sent [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
and followed it through, and even an illiterate person such as myself got it to work. *Takes a Bow* Just kidding, but seriously thanks to everyone for the help. 10+ hours and I couldn't figure it out myself!

---

