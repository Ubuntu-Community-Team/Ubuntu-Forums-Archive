---
title: "Live USB out of space?"
date: 2010-04-07
forum: General Help
---

### Post by Tehhund on 2010-04-07
I'm still cutting my teeth on Ubuntu, so this may be a little remedial. I've been successfully running 9.10 for almost a month off an 8 GB USB drive. Today when I booted, I received a message saying I had 0 bytes of free space remaining. Naturally, any attempt to write to disk has failed - for instance, when I try to install Samba or even create a text file I'm told there's no space.

I found a similar issue here: [http://ubuntuforums.org/showthread.php?t=1124328](http://ubuntuforums.org/showthread.php?t=1124328) , but they are legitimately out of space: 

> 
Filesystem           1K-blocks      Used Available Use% Mounted on

...
/dev/sdb1              3948996   3937980     11016 100% /cdrom
However, when I run df:

> # df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  2.0G  2.0G     0 100% /
udev                  849M  236K  849M   1% /dev
/dev/sda1             7.5G  2.7G  4.9G  36% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  849M  1.2M  848M   1% /dev/shm
tmpfs                 849M   20K  849M   1% /tmp
none                  849M   92K  849M   1% /var/run
none                  849M     0  849M   0% /var/lock
none                  849M     0  849M   0% /lib/init/rwLook at the /dev/sda1 line - it looks like I have nearly 5 gigs of space available.

I'll admit that I'm still learning how Linux file systems work - I don't think the 'aufs' or '/dev/loop0' entries should be causing this problem, but maybe I'm just missing something.   Can someone help me understand why it says I have no free disk space?

---

### Post by Directive 4 on 2010-04-07
aufs                  2.0G  2.0G     0 100% /

this line don't look so good.

you may find that doing a full install to the usb stick (as opposed to a live usb)

will solve these problems.

guided, use entire disk. is the option to go for.

remember to install the bootloader to the usb stick!

(you can navagate back and forth during the install process, nothing's final untill you click finish (or install? can't remember), the step before this choose advanced options, >bootloader to usb

---

### Post by Mighty_Joe on 2010-04-07
It's possible that your flash memory has "worn out".  The typical symptom is that the memory can be read but not written [(see here)]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html").  
If you can't repartition or format the drive, that's probably your issue.
If you do get the drive working and want to try a full install as suggested above, I posted links to a procedure in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") that includes some settings to improve performance and save wear.

---

### Post by jimmers on 2010-04-07
First of all you could try this tutorial from an earlier thread:-

  	 	 	 	 	 	   The following tutorial explains how to *create a larger casper-rw loop file* for your Ubuntu based [[COLOR=#009900][FONT=Lucida Grande, Verdana, Arial, Sans-Serif][SIZE=2]_flash drive_[/SIZE][/FONT][/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/#") install. For example on: Ubuntu, Xubuntu, Kubuntu, Crunchbang or Linux Mint. A larger casper-rw loop file is particularly useful for those who have performed a Linux install to a large thumb drive using a Windows USB tutorial and need more persistent [[COLOR=#009900][FONT=Lucida Grande, Verdana, Arial, Sans-Serif][SIZE=2]_storage space_[/SIZE][/FONT][/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/#") for saving changes. The default casper-rw loop file we used in the Windows USB installation tutorials is only 1GB.
 **[COLOR=#800000]Notes:[/COLOR]** You will need to perform the following steps from a booted Linux system other than the USB Linux installation. I typically boot from the Live CD and then (once the system is up and running)  insert the USB flash drive that contains my Linux install and small casper-rw.
 **[COLOR=#800000]Warning:[/COLOR]** Block [[COLOR=#009900][FONT=Lucida Grande, Verdana, Arial, Sans-Serif][SIZE=2]_file size_[/SIZE][/FONT][/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/#") must be less than < 4096 MB on a fat32 formatted flash drive due to the 4GB file size limitation of a fat32 partition.
 **Creating a NEW larger casper-rw loop file**

 The following method will create a NEW casper-rw file that will replace the old one. If you want to resize an existing image see the next section**.**
 
[LIST=1]
[*]After your up and 	running in Linux, insert the flash drive that contains your 	**casper-rw** loop file  	
[*]Open a terminal  	
[*]Type the following into the terminal window 	and press enter
 	[INDENT]**dd if=/dev/zero of=casper-rw 	bs=1M count=****[COLOR=#ff0000]1024[/COLOR]**[/INDENT] 	(replacing **[COLOR=#ff0000]1024[/COLOR]** 	with the "size in MB" you wish to use for saving changes 	persistently)  	
[*]Type the following into the terminal and 	press enter
 	[INDENT]**[COLOR=#000000]mkfs.ext3 	-F casper-rw[/COLOR]**[/INDENT]
[*]Copy the new 	**casper-rw** file to your USB flash drive  	
[*]Restart your computer, booting from the USB 	flash drive and enjoy using the larger casper-rw loop block file you 	have just created.  	
[/LIST]
 **Resize an existing casper-rw loop file**

 The following method will allow you to *resize your existing casper-rw* image (expand casper-rw). You should create a backup just in case before proceeding.
 
[LIST=1]
[*]After your up and 	running in Linux, insert the flash drive that contains your 	**casper-rw** loop file  	
[*]Open a terminal 	and change directory (CD) to the location of your casper-rw file  	
[*]Type the following into the terminal window 	and press enter
 	[INDENT]**dd if=/dev/zero bs=1M count=****[COLOR=#ff0000]1024[/COLOR]**** 	>> casper-rw**[/INDENT] 	(replacing **[COLOR=#ff0000]1024[/COLOR]** 	with the size in MB you wish to increase the original size by)  	
[*]Type the following into the terminal window 	and press enter
 	[INDENT]**resize2fs casper-rw**[/INDENT]
[/LIST]
 If all goes well, you should now have a larger casper-rw loop file to use for saving your persistent changes.
Secondly you could try this tutorial from UbuntuGeek:-
   	 	 	 	 	 	  I was reading [How to install Ubuntu Linux from USB Stick]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html") posted on this site a while ago, and found it to be quite some work to get Ubuntu working on a USB stick. Besides, having to prepare your USB device, creating a separate partition on it which will be more or less “useless” after the installation, giving up 750MB of space? 
There had to be a better way.
Together with a colleague of mine, I decided to figure out whether there could be an easier way to install Ubuntu on a USB device.
I found a way of doing it in a much simpler way… without creating the separate partition to store the LiveCD:
A couple of assumptions to take into account when going through this manual:
 
[LIST]
[*]My computer (Dell 	D820 [[COLOR=#006400]_laptop_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#")) 	has 1 internal disk, devided into 3 partitions (dell utility - 	windows - Ubuntu 8.04)  	
[*]Just one USB 	device (in my case a 250GB harddisk  	
[*]BIOS configured to enable boot from internal 	HDD, CD/DVD and USB [[COLOR=#006400]_Storage 	device_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#")  	
[/LIST]
 (I didn’t take screenshots, so I will be explaining a lot about the screens… It looks like a lot of work, but trust me: it is not, and it really is easy:smile:
 
[LIST=1]
[*]Insert the LiveCD 	into your computer;  	
[*]Connect your USB 	device;  	
[*]Boot your computer 	from the liveCD;  	
[*]Once Ubuntu is 	started, go to System - Administration - Partition Manager
This 	will open the Partion Editor. Select your USB device and delete all 	partitions on it. Click Apply and exit Partition Editor;  	
[*]Double Click the 	Install Icon. This will start the Installer;  	
[*]The Welcome Screen 	is shown. Choose your language and click Forward;  	
[*]Select your Time 	Zone and click Forward;  	
[*]Choose your 	Keyboard Layout and click Forward;  	
[*]The partitioner 	will be started, and you will be given the choice where to install 	Ubuntu. Choose Guided - Use entire disk, selecting your USB device 	(this will most likely be /dev/sdb, don’t choose /dev/sdb1!);  	
[*]The next sceen you 	will give your username/password information. Provide the required 	info and hit Forward;  	
[*]If there is 	anything to migrate from other installations on your [[COLOR=#006400]_computer_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#") 	(most likely not), do whatever you want, and click Forward;  	
[*]**The next screen 	is important** - It is titled: “Ready to Install”. **Be 	careful here: before clicking on Forward, **make sure you [B]click 	on the “Advanced” Button!
[/B]This will open a new screen, 	giving you the option whether and where to install the bootloader. 	**Select your USB device** (in my case it was /dev/sdb) to 	install the bootloader to;
Exit this screen and click on Forward 	in the “Ready to Install” screen, which will be shown;  	
[*]The installation will be started now. Just be 	patient, grab a cup of coffee and come back 15 minutes later, your 	installation will be more or less finished by then.  	
[/LIST]
 So you have finished the installation. However, when you will be restarting your system from USB, you will find out that the partition you just installed Ubuntu to cannot be mounted.
Here comes the trick:
 
[LIST=1]
[*]Once the 	installation is finished, reboot your [[COLOR=#006400]_PC_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#") 	(this is the safest) from your LiveCD, with your USB device 	connected;  	
[*]Once started, open 	up a terminal (Applications - Accessories - Terminal);  	
[*]In the Terminal, 	type: sudo -i (which will give you root privileges, so be careful 	from now on!);  	
[*]Change directories 	to /media/disk/boot/grub - This will take you to the “/boot/grub” 	directory on the USB device;  	
[*]open menu.lst with 	vi (make a backup first!)  	
[*]Go to line 130 (or 	somewhere in that area).
You will find a line looking like:
## 	## End Default options ##
And underneath it you will find three 	entries pointing to your Ubuntu you just installed:
title Ubuntu 	8.04, kernel 2.6.24-16-generic
root (hd1,0)
kernel 	/boot/vmlinuz………
initrd /boot/initrd…….
quiet
(the 	above 5 lines repeat 3 times with slight differences)  	
[*][B]The magic trick 	is to change (hd1,0) into (hd0,0) for all these three entries.
[/B]Why? 	Booting from USB device makes your USB device hd0, in stead of hd1 	at time of installation.  	
[*]Search for the 	line starting with “# groot=(hd1,0)” and change (hd1,0) to 	(hd0,0) - **Don’t delete the # at te beginning of this line!**  	
[*]Once you did this, 	you can optionally remove the remaining of the file
(everything 	underneath ### END DEBIAN AUTOMATIC KERNELS LIST);  	
[*]Save the file, 	make sure it is owned by root:ubuntu (chgrp ubuntu menu.* will do)  	
[*]Edit device.map 	(in the same directory) and change the mapping of hd0 to /dev/sdb.  	
[*]Reboot your machine, from USB, choose the 	Ubuntu installation from the Boot Loader and you are one happy 	person.  	
[/LIST]
 I guess that is it. If I missed something, please comment.
Regards,


The latter tutorial worked for using a 16 Gb Flash Drive I have all my free space,
and I am using it now as I write


Good Luck
Jim

---

### Post by dcstar on 2010-04-07
All Live USBs with persistence will eventually run out of space.

The nature of the AUFS filesystem used on these means that when a file is deleted or replaced, you never (ever) get to use that space again.

It is done deliberately so that the disk I/O is spread out on the whole the USB device, because repeatedly using the same area on these SSD devices will prematurely kill them.

The only practical "solution" I have found is to back up the data, wipe and recreate the persistent space and then restore the data. If you have a big enough persistence file to start with then you don't need to do this sort of thing too often.

There are HOWTOs on hacking configuration files to make the Live USB not use AUFS, but they look horribly complicated and aren't really worth the effort (IMHO).

---

### Post by ttguy on 2011-10-13
I had this issue too.  And if I put 2 and 2 together with the info from dcstar about how persistence always runs out of space I have a few suggestions on this matter.

When you create a Live USB instance with the "Start Up Disk Creator" the default amount of persistence is pitifully small - 128Mb.  And if what dcstar says is correct then I guess you can quickly use this up even if you don't think you are saving any thing to your stick - this is what happened to me.

You will also get misled by looking at available space on your USB stick when you mount it like a regular file system (ie when not booting from it).  My live USB was created with 128Mb of persistence and so it will report running out of space when booting from it but when looking at it as mounted as a file system it reported 3Gig free. 

So best bet I reckon is to create the live USB with a large persistence file. This file consumes your USB memory even when you have not written to it.  - Which I think is a good thing because you are not mislead about how much space you have on the stick.

---

