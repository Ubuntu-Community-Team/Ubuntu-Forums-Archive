---
title: "Dual Boot-Ubuntu/Windows 7 How To?"
date: 2010-11-28
forum: General Help
---

### Post by mastaryan on 2010-11-28
First and foremost I'm a complete nub when it comes to this.  However I'm not an idiot and I understand somethings but Linux is something I heard of since I was younger and Ubuntu is something I heard about last week!  If this information is already posted please direct me.  I've read over a lot and done all I can but I'm still stuck as I don't understand all the lingo.

Computer: Custom, 2 hard drives, each 2tb (4tb total). 4gb ram. It had Ubuntu server v8.X.X now it only has Ubuntu desktop (newest version).  No CD/DVD rom drive!:!:

What I'm trying to accomplish: Dual boot Ubuntu and WIndows 7

Background: The computer had Ubuntu server installed and I finally got the Ubuntu Desktop loaded via USB and erased the server.  I partitioned each drive.  The sda1 is partitioned 150gb of ext3, 10gb of swap and remaining NTFS.  The other hard drive sda2 is complete formated and empty space. 

Problem: When I boot to try and install Windows 7 via USB it has an issue with /Boot/BCD file. Do I have the correct partitioning on the remaining amount on my sda1?  Should it be mounted? For ext3 the root file is /.  What should the root file be for the NTFS partition?  I've followed many guides and still confused.  This week I'll be going to buy a DVD-ROM drive so I don't have to boot from USB.  Can anyone tell me what I'm doing wrong? How can I send some screen shots to help out?  

Thanks everyone and I love the Ubuntu community and I've never seen a computer load so fast.  I dread once I do get Windows installed!

---

### Post by wilee-nilee on 2010-11-28
So from a booted live Ubuntu cd or thumbdrive lets make this easiest lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

No root file it is just a NTFS partition you need at the front of the disc at best.

---

### Post by miegiel on 2010-11-28
> **mastaryan said:**
> First and foremost I'm a complete nub when it comes to this.  However I'm not an idiot and I understand somethings but Linux is something I heard of since I was younger and Ubuntu is something I heard about last week!  If this information is already posted please direct me.  I've read over a lot and done all I can but I'm still stuck as I don't understand all the lingo.

Computer: Custom, 2 hard drives, each 2tb (4tb total). 4gb ram. It had Ubuntu server v8.X.X now it only has Ubuntu desktop (newest version).  No CD/DVD rom drive!:!:

What I'm trying to accomplish: Dual boot Ubuntu and WIndows 7

Background: The computer had Ubuntu server installed and I finally got the Ubuntu Desktop loaded via USB and erased the server.  I partitioned each drive.  The sda1 is partitioned 150gb of ext3, 10gb of swap and remaining NTFS.  The other hard drive sda2 is complete formated and empty space. 

Problem: When I boot to try and install Windows 7 via USB it has an issue with /Boot/BCD file. Do I have the correct partitioning on the remaining amount on my sda1?  Should it be mounted? For ext3 the root file is /.  What should the root file be for the NTFS partition?  I've followed many guides and still confused.  This week I'll be going to buy a DVD-ROM drive so I don't have to boot from USB.  Can anyone tell me what I'm doing wrong? How can I send some screen shots to help out?  

Thanks everyone and I love the Ubuntu community and I've never seen a computer load so fast.  I dread once I do get Windows installed!

It seems to me you've done something wrong (or something went wrong) while making the windows-installation-USB. The /Boot/BCD file is probably on the USB stick. I can't really help you with that, maybe you can find some info elsewhere (like on a asus eee forum, there are alot of netbooks and laptops without CD/DVD-players these days).

When you install windows and ubuntu (or anything else) on a machine, it's best to install windows first. The windows installation overwrites the MBR (master boot record) and ubuntu will no longer boot. However if you install windows last you can repair the MBR and grub menu by booting the live-CD and running a couple of grub repair commands. A menu entry to boot windows will be added too ;)

(Consider getting a USB-DVD player)

Good luck

---

### Post by mastaryan on 2010-11-28
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets make this easiest lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

No root file it is just a NTFS partition you need at the front of the disc at best.

I did do this!  I will send it once the spouse gets off that computer.  She loves how quick it loads!  If it is better to load Windows then Ubuntu that's what I'll do.  So I need to boot using the USB Loader Ubuntu Desktop (I'm assuming this is what you call the LIVE USB?) then format the hard drive?  Install windows then install Ubuntu.  It took me forever how to understand partitioning!  Let me get you this read out first before we continue.

---

### Post by wilee-nilee on 2010-11-28
> **mastaryan said:**
> I did do this!  I will send it once the spouse gets off that computer.  She loves how quick it loads!  If it is better to load Windows then Ubuntu that's what I'll do.  So I need to boot using the USB Loader Ubuntu Desktop (I'm assuming this is what you call the LIVE USB?) then format the hard drive?  Install windows then install Ubuntu.  It took me forever how to understand partitioning!  Let me get you this read out first before we continue.

Yes always pre-format the Windows partition with gparted or a good partitioner. With W7 if you don't it will make 2 partitions a 200Mib boot and the NTFS OS, this will leave the next partition unallocated, and we don't want that eh. Pre-partitioning will put the boot and OS of W7 in one partition.

You can move the front of the partition at the front of the disc to the right, if it is Ubuntu besides the W7 load to the MBR=MS boot, you would have to probably reload grub to find that moved partition anyway.

Moving that partition left to right will take awhile maybe a couple of hours hard to say.

---

### Post by oldfred on 2010-11-28
Since you have two hard drives, you should also consider at least one operating system per drive. It keeps windows cleaner as some win7 software can corrupt grub2 in the MBR especially HP & Dell. If on its own drive it always can be booted if you have to from BIOS. Grub2 on the other drive will let you boot Ubuntu or windows. I also prefer to have windows on sda and Ubuntu on sdb.

Some with very large drives alway put a small operating system on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I have 3 drives with XP on one, and 3 versions of Ubuntu on the other two. So I can boot any drive if I have one drive fail for any reason. I also have a full Ubuntu on Flash drive just incase all my other plans fail. (I have never worn both a belt and suspenders but like to have multiple ways to boot:))

---

### Post by wilee-nilee on 2010-11-29
> **oldfred said:**
> Since you have two hard drives, you should also consider at least one operating system per drive. It keeps windows cleaner as some win7 software can corrupt grub2 in the MBR especially HP & Dell. If on its own drive it always can be booted if you have to from BIOS. Grub2 on the other drive will let you boot Ubuntu or windows. I also prefer to have windows on sda and Ubuntu on sdb.

Some with very large drives alway put a small operating system on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I have 3 drives with XP on one, and 3 versions of Ubuntu on the other two. So I can boot any drive if I have one drive fail for any reason. I also have a full Ubuntu on Flash drive just incase all my other plans fail. (I have never worn both a belt and suspenders but like to have multiple ways to boot:))

+1 this is a great idea as well, thanks oldfred.;)

---

### Post by miegiel on 2010-11-29
> **mastaryan said:**
> I did do this!  I will send it once the spouse gets off that computer.  She loves how quick it loads!  If it is better to load Windows then Ubuntu that's what I'll do.  So I need to boot using the USB Loader Ubuntu Desktop (I'm assuming this is what you call the LIVE USB?) then format the hard drive?  Install windows then install Ubuntu.  It took me forever how to understand partitioning!  Let me get you this read out first before we continue.

Live disks (on a CD or USB stick) are special kinds of installation CDs. A live CD has the whole operating system, ready to run, on the CD and you can boot from the CD like you would normally boot from a hard disk. Most live CDs have some form of linux on them but there are windows and DOS like live CDs too. Most often they are used for disk maintenance like virus removal, partitioning, restoring the MBR. The kind of stuff you want to do when you can't boot or when it's safer not to use the hard disk (like when modifying partitions).

The ubuntu desktop installation CD is a live CD, but the other ubuntu CDs aren't. It's a great tool when you break ubuntu and it's good for showing people ubuntu on their machine without installing it.

---

### Post by mastaryan on 2010-11-29
> **oldfred said:**
> Since you have two hard drives, you should also consider at least one operating system per drive. It keeps windows cleaner as some win7 software can corrupt grub2 in the MBR especially HP & Dell. If on its own drive it always can be booted if you have to from BIOS. Grub2 on the other drive will let you boot Ubuntu or windows. I also prefer to have windows on sda and Ubuntu on sdb.

Some with very large drives alway put a small operating system on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I have 3 drives with XP on one, and 3 versions of Ubuntu on the other two. So I can boot any drive if I have one drive fail for any reason. I also have a full Ubuntu on Flash drive just incase all my other plans fail. (I have never worn both a belt and suspenders but like to have multiple ways to boot:))

I thought about this.  Okay, so lets say I use gparted and delete the partition on my sda1 drive that is for NTFS.  I'll have like 1.6TB left over which I can expand at anytime for whatever I need.  On the other disk how should I partition it to be able to boot for Win7?  Partition all 2TB to NTFS?  Anything else need to be done while in GParted?  When I restart and change the boot in BIOS to boot to the second HD is there anything else I need to do?  This partitioning stuff is what has me all confused.  

I'm still waiting on the spouse to get off before I send my log over.  Also, the only reason I don't really want to use each hard drive as it's own is because I store a lot of files. I know 4TB is a lot but I got a lot of photos that I hate dragging around and plugging up 2-3 external hard drives!  So if needed can you share files between the two or shall I save some on the Ubuntu HD and transfer via USB to the Win7?  I like simplicity and less steps!:P 

Thanks again everyone! I'm pumped and bout to run the spouse out once I figure out how to partition and set up my HD for win7! GIDDY!

EDIT

**Does the unuseddrive need to be NTFS or FAT32?  Also, since I have win7 on my USB, do I need to formate the USB to FAT32 or NTFS?**

---

### Post by miegiel on 2010-11-29
> **mastaryan said:**
> ...

So if needed can you share files between the two or shall I save some on the Ubuntu HD and transfer via USB to the Win7?  I like simplicity and less steps!:P 

...

EDIT

**Does the unuseddrive need to be NTFS or FAT32?  Also, since I have win7 on my USB, do I need to formate the USB to FAT32 or NTFS?**

FAT32 is best for USB sticks up to 4GB

And you can access your NTFS and FAT32 partitions from ubuntu, but you can't access ext(2,3,4) partitions from windows (though I've heard there is software for windows so that you can access it).

For safety I think I should quote what I posted in another thread here too:

> **miegiel said:**
> When you boot the CD select "try ubuntu" instead of "install ubuntu". Once ubuntu has booted find the gParted program. With that you can resize your windows partition to make some space.

**But** before resizing you should always defragment your disks (in windows). This makes the whole process a lot safer, almost safe even.

**Still**, make sure you backup anything on the disk you would never want to loose

---

### Post by mastaryan on 2010-11-29
See attached.

---

### Post by oldfred on 2010-11-29
I do not recommend FAT for anything anymore except where your other device - camera, photo display and I recently learned xbox have to have it. FAT32 has a hard limit of a file no larger than 4GB. Backups, video files and others may be larger than that and if you copy it to FAT32 you destroy the file.

I like to keep system files small for both windows & Ubuntu. I then have separate data partition(s). I have a shared NTFS partition for data I want to use in both XP & Ubuntu like firefox profiles & thunderbird profiles & photos. When first using Ubuntu & still using XP a lot my wife would want to check email or facebook and I was in Ubuntu. Reboot to windows just for that was a hassle. Once I converted to a shared NTFS and same profiles I do not reboot much to XP anymore.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

I like to have windows in sda as it sometimes has more issues with being on sdb and booting from grub. Drive order can make a difference. Ubuntu does not care.
Some recommend disconnecting the windows drive when installing Ubuntu to prevent grub from installing to the windows drive which it does now unless you use manual partitioning and choose which drive to install grub to.

---

### Post by mastaryan on 2010-11-29
My wife seems to enjoy Ubuntu and I do too.  Basic searching and browsing online.  I'll eventually add a DVD Rom drive and Card Reader to download our photos but I need Windows for the Adobe software.  I know there is some similar to Dreamweaver and Photoshop but I don't want to use anything else at the moment.

Currently I have 161gb ext3, 11gb swap, 1.8tb ntfs on sda (in this order). NTFS is not mounted. Should I delete the NTFS and have the rest free space, /home, or expand ext3 or combo of each!

On sdb: its FREE 2.0TB-  _I'm going to use this to boot Win7_.  How do I need to partition this? Leave it free?

---

### Post by wilee-nilee on 2010-11-29
For me gparted is easier to understand as far as screen shots. Any partitioning as well should be done from the Live cd with the swap turned of if there is one. You will gparted on the live cd. Sp take screen shots of both drives and state what you want I just want to be on the safe side of helping.

---

### Post by mastaryan on 2010-11-29
My gparted will work sometimes and then other times it won't load?  Any idea why?

---

### Post by wilee-nilee on 2010-11-29
> **mastaryan said:**
> My gparted will work sometimes and then other times it won't load?  Any idea why?

Not sure why gparted isn't opening mine does with a external 2 terrabyte every time.

Really I think you should wait for oldfred to comment they have just more knowledge in general.

I realize you want to get this done but lets wait for more advice at least thats my advice, so that we have your ducks in a row so to speak. The size of the drives is unusual for what your doing on this forum at least.

---

### Post by mastaryan on 2010-11-29
Gparted screens attached. 

I still get an error when trying to install win7.  My boot/bcd file is corrupt.  I've used 3 different cds to rip win7 from.  I partitioned an external usb drive to load the setup, never recognized but the usb gets the boot/bcd file error.  I'm buying today (cyber monday) a stinking external dvd rom.  Any tips so far?

---

### Post by mastaryan on 2010-11-29
> **mastaryan said:**
> Gparted screens attached. 

I still get an error when trying to install win7.  My boot/bcd file is corrupt.  I've used 3 different cds to rip win7 from.  I partitioned an external usb drive to load the setup, never recognized but the usb gets the boot/bcd file error.  I'm buying today (cyber monday) a stinking external dvd rom.  Any tips so far?
My disk are good.  I've used my usb stick to load onto 2 laptops and 1 desktop.  Not sure my issue.  Also for my own enjoyment, I booted up the livecd and reformated my 2 disk drives.  So I had 4tb free hard drives, clean.  I then tried to install windows 7 and got the same error.  Sometime with the system? I'm getting tired of reinstall/install all the time. I'm sure it's not good.

**UPDATE**
I know see a Windows Vista uploader sdc2 loader when I start up.  I have to choose between 3-4 different items all have recoveries after them** Not sure what this is.

---

### Post by mastaryan on 2010-11-29
Still cannot boot windows.  Attached is everything I have of current.  I'm not going to do anything else except go buy a dvd-rom drive and hopefully they'll take it back since I just ordered one online.  I'll try with it and if I have no luck I'll try to install windows first then ubuntu.  I'd like to have ubuntu on one HD and windows on the other.

Thanks community!

---

### Post by mastaryan on 2010-11-29
> **mastaryan said:**
> Still cannot boot windows.  Attached is everything I have of current.  I'm not going to do anything else except go buy a dvd-rom drive and hopefully they'll take it back since I just ordered one online.  I'll try with it and if I have no luck I'll try to install windows first then ubuntu.  I'd like to have ubuntu on one HD and windows on the other.

Thanks community!

Here is my boot screen.  I choose the first option to open the desktop.


Ubuntu, with Linux 2.6.35-23-generic
Ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sdc2)

I type 'e' to edit Windows Vista (loader) and I get this:

insmod part_msdos
insmod fat
set root='(hd2,msdos2)
search --no-floppy --fs-uuid --set 04fe-f840
chainloader +1

---

### Post by oldfred on 2010-11-29
I have not installed win7, so I only know what I have heard. With win7 it will create a 100mb hidden boot/recovery partition and the main install. The reason for a separate boot is to allow you to encrypt the main install. You can create one NTFS partition and set the boot flag (active partition in windows) and it will install into just one partition. Windows has to boot from a primary partition. If you think you may ever want a second copy of windows reserve another primary partition. Windows can read from logical partitions inside the extended partition.

Windows needs lots of room as if it gets below 30% NTFS starts to slow down. With 2TB you can give it lots of room but I would still separate out the shared NTFS data partition(s) depending on what you want. You do not have to partition the entire drive initially if you do not now exactly what you want.

I see you posted just as I started my reply. Is the Vista shown from your USB, otherwise it should not be FAT. But Windows does set up a  FAT partition for installing from USB flash drives. Often Grub sees windows recovery or other partitions as Vista, not sure if windows just never updated some recovery/install code.

---

### Post by mastaryan on 2010-11-29
So far so good. I'm in the installation mode for Windows 7 finally! I went ahead and said to use the entire disk0 to install windows. disk1 will have my ubuntu. I can store my photos (most of my hd) in ubuntu since it has 1.5tb left over. I'll let you know how the process finished out. I'm sure we are not done yet but you guys have been awesome in helping me out.
 
**UPDATE 1** I'm typing this with Windows 7 Ultimate loaded! Let's try to boot Ubuntu
 
**UPDATE 2** I can't load Ubuntu. I have sda as Windows and sdb as Ubuntu. However, I did find this (attached) where Windows installed their temp partition on my Unbuntu. Is this where the grub issue comes into play? Should I delete part of disk0 and add the windows reserve up? How do I go about fixing this? Or remove Unbuntu totally and then reinstall?

---

### Post by mastaryan on 2010-11-29
Totally lost!  I just made a live usb loader again.  Searching for solutions.  If it has anything to do with terminal, I'll be completely lost.

---

### Post by Quackers on 2010-11-29
Is your bios set to boot from the first hard drive? If so, try setting it to boot from the second drive. If Ubuntu boots up run sudo update-grub and watch as grub.cfg is configured to see if the Windows loader is picked up by grub.
If it is try rebooting and choose Windows to see if it boots ok.

---

### Post by wilee-nilee on 2010-11-29
Honestly with 2 2 terrabyte hard drives I think this will be a per session menu boot from at best. My per-session to choose what to boot from is f12. You use this key prompt at power-on like you would if going to the bios.

This per-session boot could be any f key or esc or who knows which really.

It would be great if Ubuntu was first to be read and grub gave the W7 choice but I'm skeptical here with a custom computer that probably isn't really set to read 2 drives of this size.

This is all just conjecture but, may be the answers.

I'm to busy to spend anytime trying to stick with this until the end, just commenting.

---

### Post by mastaryan on 2010-11-29
No such luck yet.  I've went through the process to re-install grub2 however it still won't boot.  My first disk is Windows and the second disk is Ubuntu.  It doesn't matter which drive I choose in BIOS it still boots in Windows.  Only way I get it to boot in Ubuntu is with the LIVE USB.  That's where i did the terminal work, mounted the partition where Ubuntu was installed.  I just wish I could figure out how to remove Windows 7 System Reserved Partition off my Ubuntu drive and put it on my Windows Partition.

---

### Post by wilee-nilee on 2010-11-29
So with both HD where they are run the bootscript again from a Live Ubuntu CD. Post it in code tags or attach it as before and I will put it in the thread.

Do you understand what I meant by a per-session boot from menu? and can you get to that post bios boot from menu?

---

### Post by mastaryan on 2010-11-29
> **wilee-nilee said:**
> So with both HD where they are run the bootscript again from a Live Ubuntu CD. Post it in code tags or attach it as before and I will put it in the thread.

Do you understand what I meant by a per-session boot from menu? and can you get to that post bios boot from menu?

UHH??? Hmmm.  Not sure what you're talking about.  Sounds foreign!

I did however get Ubuntu to load and Windows not to load.  I copied from the Ubuntu drive the windows SYSTEM RESERVE to the Windows Drive.  This allowed me to load Ubuntu now I can't load Windows. I'll see if I can repair Windows. Back and forth!  

Would it be wise to run liveUSB and format both HD.  Then install Windows then Ubuntu?  I have nothing to lose. Both new systems with no files besides installation files installed.

---

### Post by wilee-nilee on 2010-11-29
> **mastaryan said:**
> UHH??? Hmmm.  Not sure what you're talking about.  Sounds foreign!

I did however get Ubuntu to load and Windows not to load.  I copied from the Ubuntu drive the windows SYSTEM RESERVE to the Windows Drive.  This allowed me to load Ubuntu now I can't load Windows. I'll see if I can repair Windows. Back and forth!  

**Would it be wise to run liveUSB and format both HD.  Then install Windows then Ubuntu?  I have nothing to lose. Both new systems with no files besides installation files installed.**

First stop trying to fix anything without our help, this makes it impossible to help you. I assume your final goal is a workable system right?

System reserve I have no idea what your talking about and I know this stuff pretty well.
[B]
Stop all the fixes and post the bootscript.[/B]

The only other thing you should be doing is figuring out the key prompt for this boot from at this time and posting the bootscript.

If you need a more concise description of this key prompt then ask.

To be honest your last statement is a big yes from me if you have nothing to loose, personally I think W7 in a usable size say 40 gigs into a pre-formatted NTFS, then Ubuntu alongside it next in a size workable. Then you have all the rest of that drive and the other to save stuff to that both OS can read from if they are NTFS partitions.

---

### Post by mastaryan on 2010-11-29
> **wilee-nilee said:**
> First stop trying to fix anything without our help, this makes it impossible to help you. I assume your final goal is a workable system right?

System reserve I have no idea what your talking about and I know this stuff pretty well.
[B]
Stop all the fixes and post the bootscript.[/B]

The only other thing you should be doing is figuring out the key prompt for this boot from at this time and posting the bootscript.

If you need a more concise description of this key prompt then ask.

To be honest your last statement is a big yes from me if you have nothing to loose, personally I think W7 in a usable size say 40 gigs into a pre-formatted NTFS, then Ubuntu alongside it next in a size workable. Then you have all the rest of that drive and the other to save stuff to that both OS can read from if they are NTFS partitions.

I'm fixing to leave for about an hour and I'll return with the bootscript.  I would like to have both on one disk, say 100GB each and then use the remaining 2900gb as storage.  I've read that you can swap back and forth.  I have a couple of programs though for Windows that take a lot of space.  Adobe CS5 Master Collection and MAS90.  The System Reserve that I keep mentioning is the partition that windows makes.  You can view it from your desktop, only under gparted or disk management.  Its around 100mb in size.  For some reason it added it to disk1 where my Ubuntu was loaded.  

Again when I return, I'll upload the bootscript and then we'll see what the best option is.  My ultimate end goal is to browse surf the internet, upload photos, and view them in Ubuntu.  I can use Office, Mas90, Adobe, and photo editing via windows.  Windows is for Work, Ubuntu is for Play!

---

### Post by oldfred on 2010-11-29
We need the boot script but it looks like you installed windows to drive 1  sdb not sda.

---

### Post by mastaryan on 2010-11-29
I reformatted and started from scratch.  I've installed Windows 7 and currently installing Ubuntu.  I've got the LIVEUSB installed and currently allocating drive space.

As of right now this is what I see:
/dev/sda
/dev/sda1 nfts (windows has 1tb)
/dev/sda5 swap (swap has 10gb)
/dev/sda6 ext3 /home (/home has 10gb)
/dev/sda6 ext3 / (/ has 909.5gb)

/dev/sdb
/dev/sdb1 nfts (104mb, it says this is Windows 7 bootloader)  
freespace 2000293mb

Since dev/sdb is Windows bootloader, should I install swap, ext3, ect. on this drive? 

I know you guys are getting sick and tired of me but I have bad OCD and can't stand the fact that I don't know what I'm doing.  You guys have been helpful.  As of right now, I won't touch anything else.  I appreciate you guys very much!

---

### Post by mastaryan on 2010-11-29
Okay, I can now boot either system but this is how I must do so. 
My previous thread shows how I have the files partitioned.  I also have the boot script attached.  

I can have sda as primary in BIOS and I get the option to choose Ubuntu, Memtest, or Windows 7 loader on sdb.  I can load Ubuntu just fine.  When I choose the Windows 7 option, it keeps restarting.  I can then go into my BIOS and change and make the SDB as my primary and Windows 7 boots just fine.  I do not have the option of booting Ubuntu.  Maybe it is something simple I'm sure and easily fixed.  For now I'm content and I know what system I need to use when I get on this computer.  Any additional input and help is appreciated and again I thank all of you for your help!

---

### Post by oldfred on 2010-11-29
Please copy and paste the results.txt into a message. Then highlight and click on the # on the right side of the edit panel at the top of the message to put it into code tags.

---

### Post by mastaryan on 2010-11-29
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,048,002,047 2,048,000,000   7 HPFS/NTFS
/dev/sda2       2,048,004,094 3,907,028,991 1,859,024,898   5 Extended
/dev/sda5       2,048,004,096 2,068,002,815    19,998,720  82 Linux swap / Solaris
/dev/sda6       2,068,004,864 2,088,003,583    19,998,720  83 Linux
/dev/sda7       2,088,005,632 3,907,028,991 1,819,023,360  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
224 heads, 19 sectors/track, 918004 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ECE0D0ECE0D0BDD0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8f7e2bed-d33b-47e1-8e94-19beba3cb821   swap                                     
/dev/sda6        09b3e5ca-336b-4ea7-805d-3ad1083e7367   ext3                                     
/dev/sda7        7b61c7e8-9553-4284-be57-fd69f89b07d6   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ACC4C52AC4C4F81A                       ntfs       System Reserved               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext3       (rw,commit=0)
/dev/sda1        /media/ECE0D0ECE0D0BDD0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set acc4c52ac4c4f81a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=09b3e5ca-336b-4ea7-805d-3ad1083e7367 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8f7e2bed-d33b-47e1-8e94-19beba3cb821 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


1787.3GB: boot/grub/core.img
1787.3GB: boot/grub/grub.cfg
1787.2GB: boot/initrd.img-2.6.35-22-generic
1787.2GB: boot/vmlinuz-2.6.35-22-generic
1787.2GB: initrd.img
1787.2GB: vmlinuz
```

---

### Post by oldfred on 2010-11-30
Not sure how windows did it. It installed the hidden 100MB boot partition on sdb with the main install on sda. You always have to have both hard drives working to boot windows. The win boot partition also has a grub4dos file/folder.

I prefer to have windows on one drive and Ubuntu on the other so each drive can be used independently in case of emergency.

Also if dual booting you should create a NTFS partition for shared data.

---

### Post by wilee-nilee on 2010-11-30
I see the problem and this is fixable but I will let oldfred do this.

The good thing is that you can boot Ubuntu I had wondered if having the grub boot file that deep into the disc was going to work. Don't do anything this is fixable.

You have my empathy in the OCD department I don't have that but I know those that do and other problems like Schizophrenia, very different but still a life changing situation.:) 

Your doing fine here it just takes awhile sometimes. If I told you how long it took me to get the hang of just some basic stuff you would probably feel better, and get a good laugh. Brutal for me trying to understand some things, wiped out 3 operating systems, it wasn't pretty.

---

### Post by oldfred on 2010-11-30
You can repair your main install in sda1 to make it the bootable partition.

I would first copy these files from sdb1 to sda1.
/bootmgr /Boot/BCD

That may work, not sure if then the BCD has to be updated, but it is still booting the same partition so that may be all that is required.
If more repairs to get BCD update:
From windows repair CD.

BootRec.exe /RebuildBcd

Info on win repairCD and how to use:
oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by mastaryan on 2010-11-30
It would be horrible to wipe out 3 systems.  Luckily I haven't gotten anything installed.  I installed Adobe Master Collection CS5 and Office but that's it. 

Every time I installed Windows it would create this separate boot file on the other hard drive.  I even partitioned out 100MB during the install hoping that it would use that space.  I'm not sure what's going on.  Yea, I even missed work yesterday because I was so frustrated.  

I can do is mount the 1TB that the NTFS (Windows) is installed and access the files in Ubuntu which is nice to be able to access files once I install save them here.  

I still have all but 100MB of a 2TB drive unused on SDB.  How should it be formated?  I'd just like to be able to boot from one window and not switch my drives in the BIOS every time.  

I've made it to work today and I'm thankful for your guys input.  Let me know how to fix this simple? issue!

**EDIT** I see oldfred has solution!  I'll try this when I get home!

---

### Post by mastaryan on 2010-11-30
> **oldfred said:**
> You can repair your main install in sda1 to make it the bootable partition.

I would first copy these files from sdb1 to sda1.
/bootmgr /Boot/BCD

That may work, not sure if then the BCD has to be updated, but it is still booting the same partition so that may be all that is required.
If more repairs to get BCD update:
From windows repair CD.

BootRec.exe /RebuildBcd

Info on win repairCD and how to use:
oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

So I copy the /bootmgr/Boot/BCD file from inside Windows or from Ubuntu?  I can mount this 100mb partition inside Ubuntu.  How exactly will I do this again?  Where will it be copied to?  I'm sure when I see it I'll figure it out.

If this works I'll let you know.  When I put the Windows CD in, I have yet to use the repair part so I'll wait.  I'll let you know tonight hopefully when I get home.

---

### Post by Quackers on 2010-11-30
Make hard drive 1 bootable in bios.
Boot from Windows 7 repair disc.
Run startup repair up to 3 times.
Should be fixed.

I don't know how you got 2 Windows boot files on sdb.

---

### Post by mastaryan on 2010-11-30
> **Quackers said:**
> 
I don't know how you got 2 Windows boot files on sdb.

I'm special! LOL!

I'll copy the files and then try the 3x repair.  I seen this somewhere on the forum as well.

---

### Post by Quackers on 2010-11-30
Hmm, it's all over the forum.
No need to copy the files if you run startup repair 3 time iirc.

---

### Post by mastaryan on 2010-11-30
> **Quackers said:**
> Hmm, it's all over the forum.
No need to copy the files if you run startup repair 3 time iirc.

When I load Windows 7, it'll say install or repair Windows.  Then what?  Last known configuration, ect. ect.?  Or just let it repair using whatever default method.  Then it installs, then repair again, installs, then repair again.  That's it?  I'll look it up to make sure but just want to be safe.  Will the Adobe and Office I have already installed be there still or will it need to be reinstalled?  I have 0MB free on SDA, should I shrink NFTS 100MB to allow it to install there?

---

### Post by Quackers on 2010-11-30
Repair. As in startup repair. As in up to 3 times - run it.

---

### Post by mastaryan on 2010-11-30
> **Quackers said:**
> Repair. As in startup repair. As in up to 3 times - run it.

Through windows 7 cd, click repair windows. Loads the cd and welcome screen to click install, instead click repair

---

### Post by mastaryan on 2010-11-30
I did the disk repair and it put my boot on the same partition.  Now I cannot load Ubuntu.  I'm sure it has something to do with the grub and that's greek to me...maybe?!  I'm typing this up on my LIVEUSB for Ubuntu.  SDC1 is my USB.

Let me know what to do! Thanks!

Here is my boot script
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,047,999,999 2,047,997,952   7 HPFS/NTFS
/dev/sda2       2,048,004,094 3,907,028,991 1,859,024,898   5 Extended
/dev/sda5       2,048,004,096 2,068,002,815    19,998,720  82 Linux swap / Solaris
/dev/sda6       2,068,004,864 2,088,003,583    19,998,720  83 Linux
/dev/sda7       2,088,005,632 3,907,028,991 1,819,023,360  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,633,407    15,633,376   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ECE0D0ECE0D0BDD0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8f7e2bed-d33b-47e1-8e94-19beba3cb821   swap                                     
/dev/sda6        09b3e5ca-336b-4ea7-805d-3ad1083e7367   ext3                                     
/dev/sda7        7b61c7e8-9553-4284-be57-fd69f89b07d6   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        207E-B99B                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/09b3e5ca-336b-4ea7-805d-3ad1083e7367 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/7b61c7e8-9553-4284-be57-fd69f89b07d6 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/ECE0D0ECE0D0BDD0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set acc4c52ac4c4f81a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=09b3e5ca-336b-4ea7-805d-3ad1083e7367 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8f7e2bed-d33b-47e1-8e94-19beba3cb821 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


1787.3GB: boot/grub/core.img
1787.2GB: boot/grub/grub.cfg
1787.3GB: boot/initrd.img-2.6.35-22-generic
1787.2GB: boot/initrd.img-2.6.35-23-generic
1787.3GB: boot/vmlinuz-2.6.35-22-generic
1787.3GB: boot/vmlinuz-2.6.35-23-generic
1787.2GB: initrd.img
1787.3GB: initrd.img.old
1787.3GB: vmlinuz
1787.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 fa 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 8b ee 00 83 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9b b9 7e 20 4e  4f 20 4e 41 4d 45 20 20  |..)..~ NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 e0 27 16 00  66 ba 00 00 00 00 bb 00  |}.f..'..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2010-11-30
Does windows boot ok. It looks like the correct files are now in the window boot partition.

You just need to reinstall grub2.

#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2 in drive sda's MBR:
#Find linux partition, change sda7 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Then after rebooting:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive (sda), enter to accept, do not choose partitions (not sdaY where Y is a number)

---

### Post by mastaryan on 2010-12-01
> **oldfred said:**
> Does windows boot ok. It looks like the correct files are now in the window boot partition.

You just need to reinstall grub2.

#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2 in drive sda's MBR:
#Find linux partition, change sda7 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Then after rebooting:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive (sda), enter to accept, do not choose partitions (not sdaY where Y is a number)

Windows loads perfect.  
I did the first part before rebooting.  No errors (see screenshot attached).  
Now before I reboot do I need to reboot within the LIVEUSB or try to boot regular? I'll wait for a response.

**EDIT**
I loaded without the liveusb.  Ubuntu loaded fine.  I did notice it said Windows 7 loader on sdb1 still however when I typed in sudo update-grub it said Windows 7 loader on sda now.  The dpkg is a different story, I kept hitting space but I think I updated it to whatever it said first.  I'm assuming I was suppose to type in sda there.  The window says if you are unsure you can load it to all your boot drives.  Oh well.  I'll wait til it finishes and then type sda and restart and see where I stand!

---

### Post by wilee-nilee on 2010-12-01
Oldfred is on line but just reboot to the grub screen you are familiar with, choose the Ubuntu install and once in open a terminal and run. 

```
sudo update-grub
```


Your not rebooting the thumb but to the actual Ubuntu install, make sure that is where you go.

---

### Post by mastaryan on 2010-12-01
> **wilee-nilee said:**
> Oldfred is on line but just reboot to the grub screen you are familiar with, choose the Ubuntu install and once in open a terminal and run. 

```
sudo update-grub
```


Your not rebooting the thumb but to the actual Ubuntu install, make sure that is where you go.

Thank you!  All is well except the dpkg package which was probably unnecessary.  I'll restart and see what happens!

++EDIT++
I hit enter twice on the dpkg screen and it did something, I think I let it default to whatever it put in there.  Thats what I done, I didn't change that value.

---

### Post by mastaryan on 2010-12-01
Now windows wants to keep rebooting.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,047,999,999 2,047,997,952   7 HPFS/NTFS
/dev/sda2       2,048,004,094 3,907,028,991 1,859,024,898   5 Extended
/dev/sda5       2,048,004,096 2,068,002,815    19,998,720  82 Linux swap / Solaris
/dev/sda6       2,068,004,864 2,088,003,583    19,998,720  83 Linux
/dev/sda7       2,088,005,632 3,907,028,991 1,819,023,360  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ECE0D0ECE0D0BDD0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8f7e2bed-d33b-47e1-8e94-19beba3cb821   swap                                     
/dev/sda6        09b3e5ca-336b-4ea7-805d-3ad1083e7367   ext3                                     
/dev/sda7        7b61c7e8-9553-4284-be57-fd69f89b07d6   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext3       (rw,commit=0)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ece0d0ece0d0bdd0
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=09b3e5ca-336b-4ea7-805d-3ad1083e7367 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8f7e2bed-d33b-47e1-8e94-19beba3cb821 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


1787.3GB: boot/grub/core.img
1787.3GB: boot/grub/grub.cfg
1787.3GB: boot/initrd.img-2.6.35-22-generic
1787.2GB: boot/initrd.img-2.6.35-23-generic
1787.3GB: boot/vmlinuz-2.6.35-22-generic
1787.3GB: boot/vmlinuz-2.6.35-23-generic
1787.2GB: initrd.img
1787.3GB: initrd.img.old
1787.3GB: vmlinuz
1787.3GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-12-01
Did you run the in a terminal
```
sudo update-grub
```

When your are in the Ubuntu install

---

### Post by mastaryan on 2010-12-01
> **wilee-nilee said:**
> Did you run the in a terminal
```
sudo update-grub
```

When your are in the Ubuntu install

I did it when I opened up Ubuntu without the LIVECD (see attached)

Windows worked before I did what oldfred said to do. Now only Ubuntu.  Wow this is frustrating!

---

### Post by oldfred on 2010-12-01
Windows booted ok when you had the windows boot loader in the MBR?

If so, it should work with grub. 

You do have a grub4dos folder in windows that may be confusing grub.
/grldr

I would from Ubuntu delete just that /grldr folder.

Everything else in the boot info looks normal.

---

### Post by mastaryan on 2010-12-01
> **oldfred said:**
> Windows booted ok when you had the windows boot loader in the MBR?

If so, it should work with grub. 

You do have a grub4dos folder in windows that may be confusing grub.
/grldr

I would from Ubuntu delete just that /grldr folder.

Everything else in the boot info looks normal.

Where do I find this folder? Windows was the only thing that ran before I did the MBR thing with mnt/..... Now only Ubuntu loads.

**FOUND IT** Deleted and now will try to load both.

---

### Post by mastaryan on 2010-12-01
Deleted and only ubuntu will load still

---

### Post by Quackers on 2010-12-01
What exactly do you mean by only ubuntu will load?
Are you getting the grub screen with the choice of operating systems to boot from?
I presume not.

---

### Post by mastaryan on 2010-12-01
> **Quackers said:**
> What exactly do you mean by only ubuntu will load?
Are you getting the grub screen with the choice of operating systems to boot from?
I presume not.

I get that screen. Ubuntu loads in 19 seconds. When I choose windows 7 it restarts my computer over and over.

---

### Post by Quackers on 2010-12-01
And you have now deleted grldr is that correct?
If yes, please run the boot script again and post the new output. Thanks.

---

### Post by mastaryan on 2010-12-01
Ok I'm typing from iPhone. Hold on let me start it back up

---

### Post by mastaryan on 2010-12-01
```
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,047,999,999 2,047,997,952   7 HPFS/NTFS
/dev/sda2       2,048,004,094 3,907,028,991 1,859,024,898   5 Extended
/dev/sda5       2,048,004,096 2,068,002,815    19,998,720  82 Linux swap / Solaris
/dev/sda6       2,068,004,864 2,088,003,583    19,998,720  83 Linux
/dev/sda7       2,088,005,632 3,907,028,991 1,819,023,360  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ECE0D0ECE0D0BDD0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8f7e2bed-d33b-47e1-8e94-19beba3cb821   swap                                     
/dev/sda6        09b3e5ca-336b-4ea7-805d-3ad1083e7367   ext3                                     
/dev/sda7        7b61c7e8-9553-4284-be57-fd69f89b07d6   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext3       (rw,commit=0)
/dev/sda1        /media/ECE0D0ECE0D0BDD0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ece0d0ece0d0bdd0
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=09b3e5ca-336b-4ea7-805d-3ad1083e7367 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8f7e2bed-d33b-47e1-8e94-19beba3cb821 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


1787.3GB: boot/grub/core.img
1787.3GB: boot/grub/grub.cfg
1787.3GB: boot/initrd.img-2.6.35-22-generic
1787.2GB: boot/initrd.img-2.6.35-23-generic
1787.3GB: boot/vmlinuz-2.6.35-22-generic
1787.3GB: boot/vmlinuz-2.6.35-23-generic
1787.2GB: initrd.img
1787.3GB: initrd.img.old
1787.3GB: vmlinuz
1787.3GB: vmlinuz.old
```

---

### Post by Quackers on 2010-12-01
All boot files for both systems seem ok now.
As oldfred suggested earlier, it may be that the grldr file was confusing the Windows loader, or it may have interfered with one of its files.
I know this is a nuisance but all I can suggest is to run the startup repair again from the Windows repair disc. Once this is done and Windows boots again it will then be necessary to re-install grub as you did before (from the live cd).
Hopefully with grldr now deleted this should fix things.

---

### Post by mastaryan on 2010-12-01
> **Quackers said:**
> All boot files for both systems seem ok now.
As oldfred suggested earlier, it may be that the grldr file was confusing the Windows loader, or it may have interfered with one of its files.
I know this is a nuisance but all I can suggest is to run the startup repair again from the Windows repair disc. Once this is done and Windows boots again it will then be necessary to re-install grub as you did before (from the live cd).
Hopefully with grldr now deleted this should fix things.

That's what I did while I was on my iPhone typing.  I went to bootrec.exe/fixmbr

Booted LIVEUSB and did the sudo update-grub again

GRLDR is not to be found.  Now I've posted this.  I'll try to restart one last time, otherwise it was fun trying to install Ubuntu, guess I'll stick with Windows. I have this computer since Saturday and yet all I've done is work on this crap.

++CRAP++ Found the GRLDR again.  It's in the /boot/grub folder.

---

### Post by mastaryan on 2010-12-01
It's not a folder, just a file.  When I try to delete it says I do not have permission.  No options to select under the permissions tab.

---

### Post by Quackers on 2010-12-01
In all honesty if you didn't jump the gun trying fixes of your own this could have been fixed 3 or 4 pages ago.
Nobody in this thread told you to try to load grub legacy, but you had grldr in sda1. 
In the last post I asked you to run the startup repair from the Windows cd and you ran /fixmbr. 
Booting from the live cd and running sudo update-grub is useless. By doing that you are trying to update grub on the liove cd!!! You need to update grub in your actual system.
If you ask for advice, the least you can do is follow it.
We are trying to help you. We have been for 7 pages!

---

### Post by mastaryan on 2010-12-01
> **Quackers said:**
> In all honesty if you didn't jump the gun trying fixes of your own this could have been fixed 3 or 4 pages ago.
Nobody in this thread told you to try to load grub legacy, but you had grldr in sda1. 
In the last post I asked you to run the startup repair from the Windows cd and you ran /fixmbr. 
Booting from the live cd and running sudo update-grub is useless. By doing that you are trying to update grub on the liove cd!!! You need to update grub in your actual system.
If you ask for advice, the least you can do is follow it.
We are trying to help you. We have been for 7 pages!

I didn't update grub in my liveusb.  I did it in the file system.  I did exactly what you said in your last post which was run the repair cd again.  It did not do anything the 3x I tried so I reinstalled the MBR.  Got grub2 running and now trying to figure out how the heck to delete grldr.  I do not have permission to do so.

This grldr isn't in my windows folder.  I found it in the file system of Ubuntu.  /boot/grub/grldr.img

---

### Post by Quackers on 2010-12-01
grldr is now gone from sda1, that is the important thing (as the output fromthe boot script shows).
If there is another one somewhere, forget it.
How did you re-install grub2? Using the --recheck command?
What happens when you boot the computer now?
If it boots to Ubuntu please open a terminal and run sudo update-grub.
Watch the terminal window to see if the Windows Loader is picked up.
If it is, please reboot and select Windows loader from the grub menu.
What happens?

---

### Post by mastaryan on 2010-12-01
> **Quackers said:**
> grldr is now gone from sda1, that is the important thing (as the output fromthe boot script shows).
If there is another one somewhere, forget it.
How did you re-install grub2? Using the --recheck command? 
What happens when you boot the computer now?  I'LL DO THIS NOW..
If it boots to Ubuntu please open a terminal and run sudo update-grub.
Watch the terminal window to see if the Windows Loader is picked up.
If it is, please reboot and select Windows loader from the grub menu.
What happens?

No need to --recheck, it did it on the first try.  I will restart and hopefully start Ubuntu.  I'll go straight and type in sudo update-grub. I'll post the picture again like in my previous post.  I'll restart and let you know what doesn't happen.

---

### Post by mastaryan on 2010-12-01
What I've done since my last post:
1.Restart computer
2.GNU GRUB version 1.98-20100804-5ubuntu3 screen loaded.  Selected the first option to load Ubuntu
3.Ubuntu loads and ask to check disk.  I let this process finish.
4.Open terminal and type sudo update-grub (see attached, note the time)
5.restart computer
6.GNU GRUB (see #2) loads.  I choose to load Windows 7 (loader) (on /dev/sda1)
7.Computer restarts, same GNU GRUB screen.  
8. Select Windows 7 (loader) (on /dev/sda1) again.
9. Computer restarts, same GNU GRUB screen.
10. Select Ubuntu and it loads up.  
11. Open terminal to type in bootscript (see attached)
12. Post bootscript (see below)
13. Type this post. Got my :popcorn: ready!

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,047,999,999 2,047,997,952   7 HPFS/NTFS
/dev/sda2       2,048,004,094 3,907,028,991 1,859,024,898   5 Extended
/dev/sda5       2,048,004,096 2,068,002,815    19,998,720  82 Linux swap / Solaris
/dev/sda6       2,068,004,864 2,088,003,583    19,998,720  83 Linux
/dev/sda7       2,088,005,632 3,907,028,991 1,819,023,360  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ECE0D0ECE0D0BDD0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8f7e2bed-d33b-47e1-8e94-19beba3cb821   swap                                     
/dev/sda6        09b3e5ca-336b-4ea7-805d-3ad1083e7367   ext3                                     
/dev/sda7        7b61c7e8-9553-4284-be57-fd69f89b07d6   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext3       (rw,commit=0)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 7b61c7e8-9553-4284-be57-fd69f89b07d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ece0d0ece0d0bdd0
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=7b61c7e8-9553-4284-be57-fd69f89b07d6 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=09b3e5ca-336b-4ea7-805d-3ad1083e7367 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8f7e2bed-d33b-47e1-8e94-19beba3cb821 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


1787.3GB: boot/grub/core.img
1787.3GB: boot/grub/grub.cfg
1787.3GB: boot/initrd.img-2.6.35-22-generic
1787.2GB: boot/initrd.img-2.6.35-23-generic
1787.3GB: boot/vmlinuz-2.6.35-22-generic
1787.3GB: boot/vmlinuz-2.6.35-23-generic
1787.2GB: initrd.img
1787.3GB: initrd.img.old
1787.3GB: vmlinuz
1787.3GB: vmlinuz.old
```

---

### Post by Quackers on 2010-12-01
Well that's all very odd. The advice that you have been given has worked hundreds of times previously. The only difference that is obvious to me is the size of your hard drives. As willee-nillee suggested some time ago, this may be an issue. I have no idea why that would be, but, who knows.
It would seem that installing grub is somehow breaking the Windows loader. I'm afraid I have no idea why that may be. It isn't normally an issue. In fact, these instructions have worked for me more than once.
It may be that someone else can come up with an answer for you. I hope they do.
For now, I'm stumped :-(
If I can think of anything I will let you know, by pm, if necessary.
Good luck to you, and I'm sorry your work has gone unrewarded.

---

### Post by mastaryan on 2010-12-01
> **Quackers said:**
> Well that's all very odd. The advice that you have been given has worked hundreds of times previously. The only difference that is obvious to me is the size of your hard drives. As willee-nillee suggested some time ago, this may be an issue. I have no idea why that would be, but, who knows.
It would seem that installing grub is somehow breaking the Windows loader. I'm afraid I have no idea why that may be. It isn't normally an issue. In fact, these instructions have worked for me more than once.
It may be that someone else can come up with an answer for you. I hope they do.
For now, I'm stumped :-(
If I can think of anything I will let you know, by pm, if necessary.
Good luck to you, and I'm sorry your work has gone unrewarded.

Looks like Ubuntu is getting uninstalled.  It's a nice system.  Maybe one day.  Imagine this also, I still have another 2TB system that isn't even allocated to anything.  Would it be worth to try and install on separate disk or f*(+ it and move on?  The only time it worked was when Windows loader was on the other HD by itself.  However then I still had to go into the bios to load windows.  It would've been nice to choose from the grub screen.

---

### Post by Quackers on 2010-12-01
To be honest, as I don't know why it's not working now, I can't really advise about the use of another drive :-)
It depends how much you are willing to do to get things working.
What you suggest could be a worthwhile venture, but if the cause is the drive's size, I wouldn't have thought a new drive would make a difference. But I could be wrong :-)
With regard to the boot partition, everything that was in that partition is now in sda1, so I can't see any difference.
Have a think about things, and if you fancy using separate drives, have a go. Please let us know what happens if you do :-)
Good luck to you.

---

### Post by Mark Phelps on 2010-12-01
> ... and if you fancy using separate drives, have a go.

THIS is what I've generally done.  It prevents all kinds of problems with the two different OSs stepping on the MBRs and boot loaders.

---

### Post by mastaryan on 2010-12-01
> **Mark Phelps said:**
> THIS is what I've generally done.  It prevents all kinds of problems with the two different OSs stepping on the MBRs and boot loaders.

I may get giddy and try this later.  At the moment, I'd like to enjoy my new computer and build this website for my baseball team.  Maybe this weekend.

---

### Post by oldfred on 2010-12-01
When you ran fixMBR did windows boot ok. Did you boot it several times to make sure?

The difference between windows booting from the MBR and grub booting windows is none. Windows jumps to the PBR or partition boot sector, grub boots and if you choose windows jumps to the PBR.

The old version of grub when windows did not work just crashed (as windows would), the new versions of grub checks that windows is working and returns if it is not. Not sure if something in there is the issue or if windows is still the problem.

Running fixMBR just loads the MBR or boot code. If windows is not booting, you have to run the full set of command line windows fixes or at the very least the auto repair 3 times.
You have to have all the boot files, the PBR or boot sector and the BCD all working correctly for windows to work.

And sometimes ever with new installs chkdsk is required.

---

### Post by mastaryan on 2010-12-02
> **oldfred said:**
> When you ran fixMBR did windows boot ok. Did you boot it several times to make sure?

The difference between windows booting from the MBR and grub booting windows is none. Windows jumps to the PBR or partition boot sector, grub boots and if you choose windows jumps to the PBR.

The old version of grub when windows did not work just crashed (as windows would), the new versions of grub checks that windows is working and returns if it is not. Not sure if something in there is the issue or if windows is still the problem.

Running fixMBR just loads the MBR or boot code. If windows is not booting, you have to run the full set of command line windows fixes or at the very least the auto repair 3 times.
You have to have all the boot files, the PBR or boot sector and the BCD all working correctly for windows to work.

And sometimes ever with new installs chkdsk is required.

I tried multiple times to boot Windows until it would freeze up.  Usually after the 3rd-4th attempt.

I assume I had the newest grub.  Should show in my boot scripts?
I also let Windows and Ubuntu to the check disk when it would start up.  

Auto repair-would you click auto repair, it do its thing and then click again or would you restart in between times?  

Attached is my current disk management screen.

---

### Post by oldfred on 2010-12-02
I have never run the auto repair and from the links I have seen the command line (even in windows:)) works better.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

I really recommend installing Ubuntu to the second drive hd1. And with huge drives like you have, you need to make smaller partitions. If you ever have a partition get corrupted having one big one can be impossible to recover from.

Some recommend disconnecting the windows drive to install Ubuntu to avoid the issues of which MBR to install grub2.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home - for the amount you want to use:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

And on the windows drive you should create a separate shared NTFS data partition. Even windows users recommend that your data be separate so when you have to reinstall windows you do not have to reinstall all your data. Regular chkdsk and backups are still required.

---

### Post by mastaryan on 2010-12-20
Its me again! What's going on this time?  I have 50GB on sdb that I wanted to use for UBUNTU.  I can't load Windows now.  All I can load is Ubuntu on my USB.  I don't have a CD-ROM drive either so running Windows repair isn't going to happen.  If it's needed then forget it.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 3244919032 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 3,907,024,895 3,907,022,848   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 3,221,227,519 3,221,225,472   7 HPFS/NTFS
/dev/sdb2       3,221,227,520 3,291,228,159    70,000,640  83 Linux
/dev/sdb3       3,326,085,120 3,907,024,895   580,939,776   7 HPFS/NTFS
/dev/sdb4       3,291,230,206 3,326,083,071    34,852,866   5 Extended
/dev/sdb5       3,291,230,208 3,314,083,839    22,853,632  83 Linux
/dev/sdb6       3,314,085,888 3,326,083,071    11,997,184  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,633,407    15,633,376   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ECE0D0ECE0D0BDD0                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0244E09044E0882D                       ntfs       Media                         
/dev/sdb2        a13de43c-8380-4c16-ab5a-018084c28f35   ext3                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        696bbbc2-5243-4a0c-a237-69bdbe4e5dc2   ext3                                     
/dev/sdb6        238faebb-52eb-4320-891e-e014217f9aaa   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        207E-B99B                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set a13de43c-8380-4c16-ab5a-018084c28f35
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set a13de43c-8380-4c16-ab5a-018084c28f35
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a13de43c-8380-4c16-ab5a-018084c28f35
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a13de43c-8380-4c16-ab5a-018084c28f35 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a13de43c-8380-4c16-ab5a-018084c28f35
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a13de43c-8380-4c16-ab5a-018084c28f35 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a13de43c-8380-4c16-ab5a-018084c28f35
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a13de43c-8380-4c16-ab5a-018084c28f35
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ece0d0ece0d0bdd0
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=a13de43c-8380-4c16-ab5a-018084c28f35 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=696bbbc2-5243-4a0c-a237-69bdbe4e5dc2 /home           ext3    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=238faebb-52eb-4320-891e-e014217f9aaa none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


1661.3GB: boot/grub/core.img
1661.3GB: boot/grub/grub.cfg
1661.4GB: boot/initrd.img-2.6.35-22-generic
1661.3GB: boot/vmlinuz-2.6.35-22-generic
1661.4GB: initrd.img
1661.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  eb 58 90 2d 46 56 45 2d  46 53 2d 00 02 08 00 00  |.X.-FVE-FS-.....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 40 c6  |........?.....@.|
00000020  00 00 00 00 e0 1f 00 00  00 00 00 00 00 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  a0 fb 7d b4 7d 8b f0 ac  |{......|..}.}...|
00000070  98 40 74 0c 48 74 0e b4  0e bb 07 00 cd 10 eb ef  |.@t.Ht..........|
00000080  a0 fd 7d eb e6 cd 16 cd  19 00 00 00 00 00 00 00  |..}.............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  3b d6 67 49 29 2e d8 4a  83 99 f6 a3 39 e3 d0 01  |;.gI)..J....9...|
000000b0  00 00 30 04 00 00 00 00  00 a0 6a 18 00 00 00 00  |..0.......j.....|
000000c0  00 50 a5 2c 00 00 00 00  00 00 00 00 00 00 00 00  |.P.,............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  00 00 00 00 00 00 00 00  78 78 78 78 78 78 78 78  |........xxxxxxxx|
000001a0  78 78 78 78 78 78 78 78  78 78 78 78 78 78 78 78  |xxxxxxxxxxxxxxxx|
*
000001e0  78 78 78 78 78 78 78 78  ff ff ff ff ff ff ff ff  |xxxxxxxx........|
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 fa 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 8b ee 00 83 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9b b9 7e 20 4e  4f 20 4e 41 4d 45 20 20  |..)..~ NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 e0 27 16 00  66 ba 00 00 00 00 bb 00  |}.f..'..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by mastaryan on 2010-12-20
:popcorn:Looks like the boot file is in my Windows NFTS partition?  I don't boot from this partition for Windows, its in sda.  Anyways, continue on.  I'm re-reading this thread to see what I can possibly do.

**SEE ATTACHED**
You can see what I typed when I done something with the grub.

---

### Post by oldfred on 2010-12-20
Are you booting sda or sdb. It will probably be impossible to tell from BIOS with two identical drives. I have two 160GB drives and sometimes just have to try the other one in BIOS to get the boot loader that I want.

If you boot sda, it looks like you should boot the install on sdb2. It would be a little better to have the grub on sdb, but lets see if you can boot first.

---

### Post by mastaryan on 2010-12-20
sda is my windows boot.  When I created my partitions I said to boot Ubuntu from sdb2.

---

### Post by mastaryan on 2010-12-20
When I choose to install beside existing system?  I chose to install manually the first time.

---

### Post by oldfred on 2010-12-21
Have you tried booting from sda? Or tried booting from both 2TB drives?

The install graphic you posted showed you trying to install grub to sdb2. That is not correct. You want to install to sdb. (no partition numbers)

First mount the partition - sdb2 with all the rest of the grub files.
```

sudo mount /dev/sdb2 /mnt
```

Then install grub2 to the MBR of the sdb drive.

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

You should copy the above commands to avoid typos.

then try booting either 2TB drive.

---

