---
title: "Installing on a Flash Drive"
date: 2010-07-31
forum: General Help
---

### Post by cufflink87 on 2010-07-31
Just a quick question... I know that it is possible to install ubuntu on a flash drive, but is there any way to install the full OS and not just a "liveCD" OS?

---

### Post by oldfred on 2010-07-31
It is best if you have a larger 8 or 16GB flash drive. It really is just another install to a separate drive. With separate drives you need to make sure grub2 is installed to the second drive's MBR with the advanced button. Some special settings may help if you are going to use the flash a lot.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

I just found out that you can install ext4 without the journal which should be slightly better than ext2. You should not have a journal on flash as it will wear out fastest. (I lost the link on how to do it:()

---

### Post by -kg- on 2010-07-31
> **oldfred said:**
> I just found out that you can install ext4 without the journal which should be slightly better than ext2. You should not have a journal on flash as it will wear out fastest. (I lost the link on how to do it:()

According to my research, you should be able to do it using the "tune2fs" command.  From my research (and the tune2fs man pages) the command you would need to issue is:

> tune2fs -O ^has_journal /dev/sda1

You will need to change the "sda1" to whatever the partition indicator is on your Flash Drive, like "sdb1" or sdc1", and if you're going to install more than one partition (like a /home partition) you will need to do the same to any other ext3/4 partition, as well.  The only one you can ignore is swap.  Swap never has a journal.

All the options, etc., are contained in the man pages for tune2fs for your perusal.  Looks like an interesting tool.

---

### Post by C.S.Cameron on 2010-07-31
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
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
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by JustinR on 2010-07-31
If you buy a good flash drive - the journaling shouldn't matter.

---

### Post by gordintoronto on 2010-07-31
> **cufflink87 said:**
> Just a quick question... I know that it is possible to install ubuntu on a flash drive, but is there any way to install the full OS and not just a "liveCD" OS?

The LiveCD *is* the full OS. People generally add applications.

---

### Post by JustinR on 2010-07-31
> **gordintoronto said:**
> The LiveCD *is* the full OS. People generally add applications.

Some applications and drivers like 'bcmwl-kernel-source' aren't compatible if you just put the live-cd on a flash drive (eg. using Start Up Disk Creator) because the Live-CD root file system structure is different from that of a full install.

So your safer doing a full install on a flash drive if you have adequate space.

---

### Post by gordintoronto on 2010-08-01
Thanks, I didn't know that!

---

