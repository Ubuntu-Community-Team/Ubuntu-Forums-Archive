---
title: "Anyone run Ubuntu 10.10 off a flash drive?"
date: 2010-10-16
forum: General Help
---

### Post by SNYP40A1 on 2010-10-16
My work laptop is a decent machine, but the software they put on it really makes it suck.  It can't even access all the memory due to 32-bit OS.  I'd like to install Ubuntu 64-bit on a USB flash drive and then boot off the flash drive to use Ubuntu at home.  Note that I don't want to merely clone the liveCD, I actually want to install Ubuntu onto the Flash drive (partition / format it, setup swap space, etc.) such that I have a persistent OS (save accounts, download programs, etc.).  Has anyone done this?  I'd like to know it for sure can be done before buying the flash drive.

---

### Post by 3rdalbum on 2010-10-16
It can be done, but your flash drive may turn to junk pretty quickly (6 months maybe). I would recommend buying a USB hard disk instead of a flash drive, because flash drives are not designed for this sort of load.

---

### Post by E-call on 2010-10-16
As far as I know you can set up a presistence mode on the live USB drive and it probably wont be as bad for the USB flash disk itself.
 
when I installed ubuntu 10.04 on a USB stick last week I set up a persistence mode and all my settings and everything get saved. You should look into that.
You would need at least a 4gig drive possibly an 8 would be better.
 
 
/edit
 
Im installing Ubuntu 10.10 with a 2gb persistence session now Ill test it out and see how it works.
 
You can download the program for the installer at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/).
it will allow you a persistence session of 1,2, or 4 gb

---

### Post by SNYP40A1 on 2010-10-16
> **3rdalbum said:**
> It can be done, but your flash drive may turn to junk pretty quickly (6 months maybe). I would recommend buying a USB hard disk instead of a flash drive, because flash drives are not designed for this sort of load.

I understand that the cheap 4 GB drives would not be designed for that, but some drives such as this one look like they would be made for it and in any case, offer a lifetime warranty.  So if it dies, just send it back for a new one...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820220504](http://www.newegg.com/Product/Product.aspx?Item=N82E16820220504)

Would it be safe to run Ubuntu off that drive?

---

### Post by SNYP40A1 on 2010-10-16
[http://www.youtube.com/watch?v=MSHB8-dBI2w](http://www.youtube.com/watch?v=MSHB8-dBI2w)

---

### Post by E-call on 2010-10-17
Here's a heads up, I just finished playing around with my persistent USB Ubuntu 10.10. Everything looks god all my settings etc. get saved and I ran around to 4 different computers to check it out. All my files came with it.
 
So you do not need to do a full OS install just get the prog I linked in my previous post and set up a persistent drive on the USB. SWAP etc will be handled automatically by the OS on load and it will be less demanding on your USB drive. When you save file and you want to keep em with you make sure they get saved to the casper rw drive which is the persistent portion of the USB.
 
I used 10.04 as a recovery console for broken Windows XP machines at my office and Im sure there are a lot more things you can do with it.
 
The USB you linked above should be fine. As long as your on a USB 2.0 device it should not be too slow.
 
The nice thing though is you can just image the USB drive out and save it somewhere else in case the drive does go bad. But for 20 bucks who is complaining? amirite?
 
hope this helps to answer some of your questions. cheers :P

---

### Post by C.S.Cameron on 2010-10-17
I have been running a Full install of Ubuntu from flash drive for over 3 years without problem.
There is not that much advantage over a Persistent install except that you can update and upgrade and install proprietary drivers.

Have only heard of one person complaining about wearing out a flash drive doing this and not sure that was the real reason his drive failed.

Do the math:
A flash drive is good for 10000 - 100000 writes.
At 10 minutes / gig write speed it takes 160 minutes to fill a drive.
160 minutes x 10000 = 26667 hours = 667 work weeks.
My mechanical drives don't last that long.

For actual test results see:
[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by elvino on 2010-10-17
I am a very keen supporter of running Ubuntu from a flash drive. And 10.10 is no exception. EXCEPT: I really don't like having to click 'TRY' every time I reboot. Anyone have a work-around for that problem?

---

### Post by C.S.Cameron on 2010-10-17
> **elvino said:**
> I am a very keen supporter of running Ubuntu from a flash drive. And 10.10 is no exception. EXCEPT: I really don't like having to click 'TRY' every time I reboot. Anyone have a work-around for that problem?

You could try a Full install.
Following step by step for 10.10:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by 3rdalbum on 2010-10-17
The drive I killed doing this was an 8 gig Corsair flash voyager. Very similar to the one you linked to. Lifetime warranty. Mine was in a home server so it was running 24/7 serving data off an HDD.

---

### Post by dtfinch on 2010-10-17
The test I'd like to see is filling up the entire drive once, then writing the to the same file over and over to see how long it takes to fail.

You can get that sort of behavior on a normal system just in /var/log. If say, you have multiple network interface and dhcp enabled on all of them, but one of them isn't plugged in, dhclient will write several log entries a minute complaining about it. And each metadata update (file size and modified date) means rewriting the same sector over and over.

As far as wear leveling, it really varies. If it's zoned, the erase pool is going to effectively be much smaller. [This SanDisk document](http://www.sandisk.com/Assets/File/OEM/WhitePapersAndBrochures/RS-MMC/WPaperWearLevelv1.0.pdf) describes pretty much the worse case scenario. Zones of 32 blocks of 128kb, plus an erase pool of just one block in each zone. So if you're rewriting the same block over and over, it's just going back between the same two blocks, hardly better than no wear leveling at all, just enough for marketing purposes.

[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes) - Reducing disk writes

---

### Post by C.S.Cameron on 2010-10-17
> **3rdalbum said:**
> The drive I killed doing this was an 8 gig Corsair flash voyager. Very similar to the one you linked to. Lifetime warranty. Mine was in a home server so it was running 24/7 serving data off an HDD.

How long did it last?
Was it still readable after?

---

### Post by orthello on 2010-10-18
I'm running Ubuntu in persistent mode from a Dane-Elec 4GB USB bar/stick on a daily basis for 2+ years now. Up till now I haven't experienced any unpredicted behaviour or errors.

Bottom line: USB sticks *can* be used as main media for a longer period of time, although the write capabilities are limited.

---

### Post by Grenage on 2010-10-18
We've not experienced any problems with running an OS from flash discs.  Considering their cost and resilience, they're not a bad option.

---

### Post by SNYP40A1 on 2010-10-23
Update: The flash drive arrived today and I installed Ubuntu on it.  I'm now using my work laptop running Ubuntu on the flash drive.  It's so much better than running that virus-box crap IT puts on it.  The system feels much more lightweight.  I would say that overall, the USB flash drive transfers data slower than even a disk-based drive (I'm using a Patriot XPorter Boost drive 200x speed which is supposed to be pretty fast).  I think the issue is that the flash drive has no cache.  So although it has high-throughput if the data is setup right, it's random access times are not that great.  However, the system still feels faster.  When using it.  Probably partly because using the 64-bit edition just gave me an extra 1 GB of memory that I didn't have under WinXP 32-bit.

Question: Does anyone know how to disable the hard drive when booting off flash drive?  To save power, I'd like to not even power it up.  I removed it tonight for the installation of Ubuntu.

---

### Post by oldfred on 2010-10-23
Did you adjust settings to reduce writes?

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)

---

### Post by krismx6920 on 2011-01-12
I'm thinking of buying the xporter flash drive.. just curious how it has worked out for you over the past several months?

---

