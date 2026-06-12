---
title: "partitioning for Vista / Precise Pangolin dual boot"
date: 2012-05-25
forum: General Help
---

### Post by hopefulkayaker on 2012-05-25
I know it's odd, but because the only Windows license I currently have is Vista, my 'Linux - Windows dual boot' will include Vista, not 7.

Anyway, I've only ever done rather simple partitioning - like making a data partition with Vista, using Partition Magic, as well as having Ubuntu suggest a partition setup iirc, when I wiped Vista and installed Ubuntu (10.10 at the time).

I have a 500GB HDD, and I'm thinking of the following setup for partitions:

- 150GB, Windows Vista (ntfs)
- 150GB, data partition (ntfs)
- 150GB, Ubuntu 12.04 Precise Pangolin (ext4)
- 6GB, swap space

What I'm a bit lost on is when and how I should create the above set of paritions. My system is currently running just Precise, and since I heard Windows likes to be installed first in a dual-boot setup that I will have Vista reformat the entire disk, and then reinstall Precise afterward. I will, of course, be backing up my data prior to doing this.

---

### Post by oldfred on 2012-05-25
Nothing major wrong with your partitioning, each of us has different needs or desires. I find my own optimal partitioning is not so good a year or two later.

I prefer smaller / (root) partitions. And somewhat similar smaller system partition for Windows, but Windows needs a lot more space than Ubuntu.

If most of your data is in your shared data partition you do not need a separate /home that I often suggest. But my old shared NTFS partition gets little new data as I almost never boot XP and most is going into my data (ext3) partition.

With dual booting and shared data hibernation can be dangerous, so if you have 6GB of RAM you do not need 6GB of swap. I still like some swap but you may never use it unless you edit videos.

Do not use Windows to create partitions as it may convert to dynamic if you try to create more than 4. Dynamic does not work with Ubuntu. Use Windows only for the NTFS partition or resizing the NTFS partition. Make sure Windows works with whatever final size you make it and make a boot repair CD or USB. Also best to make a full backup after you have reconfigured it to your liking.

Use gparted to create Linux partitions.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
You can also try downloading and installing the FREE version of Partition Wizard in Win7. It may allow you to safely shrink the Win7 OS partition more than does MS.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Erik1984 on 2012-05-25
Do you intend to shared data like music, videos and pictures between Ubuntu and Windows? In that case I'd suggest to decrease both the root partitions (like oldfred mentioned) in size and increse the NTFS data partition.

---

### Post by hopefulkayaker on 2012-05-25
Ah yes, good question. I do not intend to share that data between OSs. My intention in seeing how I like dual booting is to use Windows primarily for gaming as well as a few random Windows-only apps like the Fried Cookie Ringtone Maker, which is supposed to be pretty neat. I will use Precise for everything else basically - video, music, web browsing, IM, etc.

Also, I don't have much in the way of data. Currently My data is 60GB, which is why I decided to give the OSs as much space as I did in my above plan.

oldfred - thank you for the links! That is quite helpful.

---

### Post by Mark Phelps on 2012-05-26
Unless you store lots of personal data, including game settings, in the Windows OS partition, 50GB will be more than enough space to last you a long time.  There's no value to giving up 100GB of space to the Windows OS partition, unless you really need it.

---

### Post by hopefulkayaker on 2012-05-30
OK, so I shrank mu Vista partition, which went alright but not ideal. It limited the amount I could shrink it. It could only get it for to 270GB rather than 150. Oh well, not the end of the world.

Next I tried to install Precise. I haven't used USB sticks in a while, and don't currently have a CD burner atm, believe it or not. So I assumed I could just use the ISO from Windows and install that way.

I torrented the ISO image, and ran "Wubi". Not sure what the name is about. It told me it needed to reboot, and I chose the bottom 'boot helper' option since I'm not using physical media.

I rebooted, and it booted into Ubuntu by default. But one of the first things I see is this:

**(initramfs) Unable to find a medium containing a lvie file system**

Say what now?

---

### Post by oldfred on 2012-05-30
LInks here to instructions for installing to USB flash drive from both Ubuntu & Windows.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
You can also try downloading and installing the FREE version of Partition Wizard in Win7. It may allow you to safely shrink the Win7 OS partition more than does MS.

If you create NTFS primary partition with boot flag, Windows will install just to that partition.

---

