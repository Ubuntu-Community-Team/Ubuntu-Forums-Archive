---
title: "Disk corruption after power failure"
date: 2011-01-14
forum: General Help
---

### Post by Jimmy9pints on 2011-01-14
Hi, I thought I could sort this out myself, but it turns out I need the community's help!

While using my computer the other day (I was sending an email) it suddenly turned off. I didn't get any low power warning, but I was running on battery and had my iphone charging from a USB port. 

As I didn't think there was low battery, I just turned it back on again. As it was booting I saw the battery light flashing, indicating low power. I went to get the charger, but before I got it, mid boot-up it turned off again. 

This seemingly damaged something hard-disk-wise. 

Upon turning it on again it dropped into busy box with some message similar to this:
> No init fount. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)

That's not the actual message (copy pasted from another post) but the message is VERY similar to that. 

If I "exit" busy box, I get a load of message about "kernel panic" before it freezes up. 

I have booted a live USB (what I am using now). I thought since it wasn't cleanly unmounted, simply mounting and unmounting would do the trick. I was wrong. 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x561f8bbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       30402   224664577    5  Extended
/dev/sda5            2432        2681     1998848   82  Linux swap / Solaris
/dev/sda6            2681       30402   222664704   83  Linux

Disk /dev/sdb: 3868 MB, 3868430336 bytes
32 heads, 63 sectors/track, 3747 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ee37940

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3747     3776944+   b  W95 FAT32

```

sda is the main hard drive, sdb is the USB I am using. 

So I tried to unmount the hard drive.

```
ubuntu@ubuntu:~$  sudo umount /dev/sda
umount: /dev/sda: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted

```
However, it won't mount either. 
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sdatemp/
```
Previously, this was reporting that the device was already mounted, busy, or being exclusively used by a process. Now the terminal just hangs. 
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sdatemp/
^C^C
```
ctrl C doesn't cancel the operation. 

I had previously ran e2fsck (after checking it was unmounted) but it wouldn't run also because it was reporting that the device was already mounted, busy, or being exclusively used by a process.

**I don't want to do any more for fear of causing further damage. **

I am astounded that such damage can be caused so easily!

If you can, please help!

Regards,

Jimmy

---

### Post by Quackers on 2011-01-14
In gparted on the live cd desktop, can you right-click on sda1 and select "check" and then click on the green tick to apply the change. This should run a file system check and fix any errors - hopefully. Sometimes an improper shutdown renders the file system unusable.
Maybe try it on sda6 as well.

---

### Post by vanadium on 2011-01-14
What is the file system on the affected drive? What does "sudo blkid" report?

Can't you not run fsck from a live session?

I can imagine that a file system without journaling (e.g. ext2) could be totally ruined by a power outage at the wrong moment. Chances for fatal damage would be far less for a journaled file system. What you experience may also reflect a hardware failure.

---

### Post by Jimmy9pints on 2011-01-14
Thank you both for your quick replies. Here's the blkid output:

> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="c6c3581b-b432-7948-8d3f-96db5944d4c8" TYPE="ext2" 
/dev/sda1: UUID="4325daab-2549-424f-a0c4-2fc6c7787a18" TYPE="ext4" 
/dev/sda5: UUID="05d7a5b5-08f9-4c4d-99e1-fc55bcef0fb5" TYPE="swap" 
/dev/sda6: UUID="6fa93cd3-3867-49ba-88f1-58b6d5b3614f" TYPE="ext4" 
/dev/sdb1: LABEL="PENDRIVE" UUID="C08D-F9CE" TYPE="vfat" 


By the way, for anyone else suffering this problem, here are some useful threads and pages:
[http://ubuntuforums.org/showthread.php?t=1386549](http://ubuntuforums.org/showthread.php?t=1386549)
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[http://ubuntuforums.org/showthread.php?t=1606975](http://ubuntuforums.org/showthread.php?t=1606975)
[http://art.ubuntuforums.org/showthread.php?t=1601810](http://art.ubuntuforums.org/showthread.php?t=1601810)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1633183](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1633183)
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)
[http://superuser.com/questions/32467/ext3-drive-will-not-mount-after-power-failure-how-to-recover-files](http://superuser.com/questions/32467/ext3-drive-will-not-mount-after-power-failure-how-to-recover-files)
[http://www.*****************/data-recovery-articles/power-outage-and-linux-file-system-corruption-1039294.html](http://www.*****************/data-recovery-articles/power-outage-and-linux-file-system-corruption-1039294.html)

---

### Post by Jimmy9pints on 2011-01-14
> gparted on the live cd desktop, can you right-click on sda1 and select "check" and then click on the green tick to a....gparted on the live cd desktop, can you right-click on sda1 and select "check" and then click on the green tick to a

it warns of potential data loss. What are the chances and what's the most straight forward way to back up at this point?

---

### Post by Quackers on 2011-01-14
If the file system won't mount I think backups are going to be difficult. I may be wrong though :-)  I have been before!

---

### Post by Quackers on 2011-01-14
I just tried the same thing on a spare ext4 partition and I got the same warnings and I know there is nothing wrong with that file system.

---

### Post by Jimmy9pints on 2011-01-14
Tried it. Got this message.

> An error occurred while applying the operations
See the details for more information.

IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.

---

### Post by Quackers on 2011-01-14
Did you click on the details? What are they?

---

### Post by Jimmy9pints on 2011-01-14
Here's the output of that. (attached txt)

Same as the command line output.

---

### Post by Quackers on 2011-01-14
Is sda1 your /root partition?

---

### Post by Jimmy9pints on 2011-01-14
Yes, it's "/"

---

### Post by Quackers on 2011-01-14
I'm no expert on interpreting this kind of thing, but it seems to me that the file system thinks it's still open. I'm afraid I don't know what to do about that.
I am hopeful that somebody here knows what to do about it :wink:

---

### Post by Rubi1200 on 2011-01-14
Couple of things I would like to suggest:

From the LiveCD:

1. post the output of ```
sudo sfdisk -V
``` and ```
sudo fdisk -lu
```

2. run the boot info script linked at the bottom of my post and get the results back here

Thanks.

---

### Post by Jimmy9pints on 2011-01-14
Thank you very much for your effort anyway. Really appreciate it!

---

### Post by Quackers on 2011-01-14
You're welcome!
Did you see Rubi1200's post above your last?
Reinforcements have arrived :-)

---

### Post by Jimmy9pints on 2011-01-14
> reinforcements have arrived
Indeed!

Thanks.

Here's sfdisk -V

> ubuntu@ubuntu:~$ sudo sfdisk -V
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 1 does not end at a cylinder boundary
Warning: partition 1 does not end at a cylinder boundary


and fdisk -lu

> 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x561f8bbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2        39065598   488394751   224664577    5  Extended
/dev/sda5        39065600    43063295     1998848   82  Linux swap / Solaris
/dev/sda6        43065344   488394751   222664704   83  Linux

Disk /dev/sdb: 3868 MB, 3868430336 bytes
32 heads, 63 sectors/track, 3747 cylinders, total 7555528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ee37940

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7553951     3776944+   b  W95 FAT32

Ok I am going to be offline for a few hours now, but I'll be back on this later tonight.
Thanks for your continued support.

---

### Post by amsterdamharu on 2011-01-14
I guess sda1 realy isn't mounted and the following command doesn't provide any output:

```
sudo mount | grep sda1
```

The only thing I could find with "Filesystem mounted or opened exclusively by another program?" are very old posts about evms (volume management) messing up the partition as it's keeping it sort of locked.

You might try to download tinycore linux and put it on a cd (or usb with unetbootin) and see if that can do the fsck for you. Just in case one of Ubuntu's "tools" or "deamons" causes this problem. There is a volume management kernel header I could find but don't know if that would cause such a problem.

---

### Post by Rubi1200 on 2011-01-14
The odd things is this; normally fdisk -lu gives a clearer picture of whether partitions are misaligned etc.

Here, it seems fine, but sfdisk -V is reporting a problem.

We will try and find more help in the meantime.

---

### Post by Jimmy9pints on 2011-01-14
You're right ```
sudo mount | grep sda1.
``` gives no output. 

I am lost. 

I guess I can't even do a clean install while the disk is in this state.
:icon_frown:

---

### Post by Jimmy9pints on 2011-01-14
> run the boot info script linked at the bottom of my post and get the results back here


Didn't see that. Will run that as soon as I can download it.

---

### Post by Jimmy9pints on 2011-01-14
> ubuntu@ubuntu:~/Downloads$ sudo ./boot_info_script055.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 

How long is this meant to take? It's been like that for 10 minutes.

---

### Post by Rubi1200 on 2011-01-14
It should only take a minute or two.

I think there is definitely damage with the file-system and I am still looking for a solution for you.

---

### Post by Jimmy9pints on 2011-01-14
> It should only take a minute or two.

ran it for over half an hour - it never completed. 

> I am still looking for a solution for you.

Thank you

---

### Post by Quackers on 2011-01-14
I have asked somebody who is hard drive wise for any ideas on your problem.

---

### Post by srs5694 on 2011-01-14
I have a few thoughts, but I can't claim to know the precise solution. My thoughts:


[list]
[*]First and most importantly, if the data on the disk are important, *back up the partitions now!* You can do this with dd, as in "dd if=/dev/sda1 of=/mnt/sda1-backup.img". You'll need another disk mounted at /mnt (or wherever) with enough space to hold the raw partition image. If you do this, you'll be able to restore by reversing the if= and of= options, should the need arise. You can also use e2fsck and other utilities directly on the backup, in case you can't fix the access problems in any other way.
[*]It's almost certainly *not* a partitioning problem; it almost certainly *is* a filesystem problem. Thus, fdisk and sfdisk output will not be diagnostic. The fact that one complained about misaligned partitions and the other didn't is irrelevant.
[*]It might be worth trying [System Rescue CD](http://www.sysresccd.org) or [Parted Magic](http://partedmagic.com) for recovery, since they're less likely to try to auto-mount disk partitions than an Ubuntu live CD. It could be that the Ubuntu CD is trying to auto-mount, or at least identify the filesystems on, the disk's partitions and this is causing the access problems by tying up the disk when the identification/mount process hangs.
[*]You could try "lsof | grep sda1" to try to identify what's using /dev/sda1 and kill it.
[*]Try perusing the e2fsck man page. I didn't see any obvious options to get around the access problems, but I may have missed something.
[*]It's probably safer to work with the command-line tools (e2fsck, etc.) rather than GParted. You'll also have finer control over what they do -- you can use unusual options directly that might not be supported by GParted.
[/list]

---

### Post by Jimmy9pints on 2011-01-14
Thanks for your excellent and detailed reply. I'll be working on that and tell you how things go.

---

### Post by Jimmy9pints on 2011-01-14
> You'll need another disk mounted at /mnt (or wherever) with enough space to hold the raw partition image.

I am wondering how much space I'll need. Will it back up the entire partition or just the space that is being used. 

The entire disk is 250G. Roughly 18.5G for root and roughly 212G for home. Only 4G and 22G of those are used respectively. 

If I want to back up my root and home partition, will it require 250G (the size of the entire disk)? If so, it means going out and buying a new disk in order to back this one up. 

If we're only talking about backing up 26G then I can probably manage.

> It might be worth trying System Rescue CD or Parted Magic for recovery

Downloading System Rescue CD on my wife's computer right now. Interestingly, the link you gave is blocked from China (where I am) but luckily Source Forge is not. 

[Ubuntu rescue remix]("http://ubuntu-rescue-remix.org/") looks good too. 

Will try
> lsof | grep sda1I guess that isn't going to do anything to the hard drive (so shouldn't do any further damage), just check what's using it. Right?

Here's the output:
> ubuntu@ubuntu:~$ sudo lsof | grep sda1
lsof: WARNING: can't stat() vfat file system /casper-rw-backing
      Output information may be incomplete.
lsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda1  374       root  cwd       DIR       0,16     2048          2 /
jbd2/sda1  374       root  rtd       DIR       0,16     2048          2 /
jbd2/sda1  374       root  txt   unknown                                /proc/374/exe

---

### Post by Jimmy9pints on 2011-01-14
oops...double post

---

### Post by amsterdamharu on 2011-01-15
Here is some interesting reading for you: [http://art.ubuntuforums.org/showthread.php?t=1601810&highlight=mounting+dev+on+root+dev+failed+no+such+file+OR+directory&page=4](http://art.ubuntuforums.org/showthread.php?t=1601810&highlight=mounting+dev+on+root+dev+failed+no+such+file+OR+directory&page=4)  I wonder if fsck worked when run from a tinycore live CD/USB.  When using dd in combination with gzip the empty space and data of the disk will be compressed.

---

### Post by srs5694 on 2011-01-15
> **Jimmy9pints said:**
> I am wondering how much space I'll need. Will it back up the entire partition or just the space that is being used. 

The dd utility does a raw disk copy, so you'll need as much space as the partition is big. (That said, piping it through gzip can save space.)

I'd start with your root (/) partition. If you can recover it, try booting. If booting at that point fails or if you can't fix your /home partition, then tackle /home in the same way. This approach means you might not need to buy a big backup drive.

re: lsof:

> I guess that isn't going to do anything to the hard drive (so shouldn't do any further damage), just check what's using it. Right?

Correct. The lsof command just lists what files are open.

> Here's the output:

In the future, please post text output from commands in [noparse]```
[/noparse] blocks, not [noparse]> [/noparse] blocks. In the latter, the text doesn't appear in replies without cutting and pasting. [noparse][code][/noparse] blocks also preserve the formatting of the original, which is sometimes important. In any event, I'm cutting, pasting, and reformatting the below....

[quote][code]ubuntu@ubuntu:~$ sudo lsof | grep sda1
lsof: WARNING: can't stat() vfat file system /casper-rw-backing
      Output information may be incomplete.
lsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda1  374       root  cwd       DIR       0,16     2048          2 /
jbd2/sda1  374       root  rtd       DIR       0,16     2048          2 /
jbd2/sda1  374       root  txt   unknown                                /proc/374/exe
```

That's rather odd. I'm not sure what the deal iw with /casper-rw-backing and /cow. Do you have any filesystems or mount points with those names?

The last three entries provide a clue: jbd2 is the version of the journaling block device used by ext4fs. This is a part of the filesystem driver. So it looks like the computer may be trying to mount the filesystem, but something about the journal is causing it to hang. This in turn suggests at least one possible solution (namely, using tune2fs to remove the journal), but I wouldn't recommend attempting that unless and until you try with System Rescue CD or PartedMagic and can't get it to work.

---

### Post by Jimmy9pints on 2011-01-16
> **amsterdamharu said:**
> Here is some interesting reading for you: [http://art.ubuntuforums.org/showthread.php?t=1601810&highlight=mounting+dev+on+root+dev+failed+no+such+file+OR+directory&page=4](http://art.ubuntuforums.org/showthread.php?t=1601810&highlight=mounting+dev+on+root+dev+failed+no+such+file+OR+directory&page=4)  I wonder if fsck worked when run from a tinycore live CD/USB.  When using dd in combination with gzip the empty space and data of the disk will be compressed.

Very interesting reading indeed. 

I haven't gone down the Slax route, but I am currently using Systemrescue CD. 

e2fsck still gives:

```
root@sysresccd /root % e2fsck /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```

---

### Post by Jimmy9pints on 2011-01-16
Thanks!
> **srs5694 said:**
> The dd utility does a raw disk copy, so you'll need as much space as the partition is big. (That said, piping it through gzip can save space.)

The correct procedure according to what you're saying and the links the previous poster provided is use Slax or some distro that won't try to automatically mount my partitions. Then use dd to make a back up. I'll likely be able to run e2fsck on that img file. Then, place the fixed file back onto the original partition. 

The problem is I don't have a disk that size and going out and buying one is costly in both money and time. At this stage, I am thinking of ways to cut my losses. 

> **srs5694 said:**
> I'd start with your root (/) partition. If you can recover it, try booting. If booting at that point fails or if you can't fix your /home partition, then tackle /home in the same way. This approach means you might not need to buy a big backup drive.



> In the future, please post text output from commands in [noparse][code][/noparse] blocks, not [noparse][quote][/noparse] blocks. In the latter, the text doesn't appear in replies without cutting and pasting. [noparse][code][/noparse] blocks also preserve the formatting of the original, which is sometimes important. In any event, I'm cutting, pasting, and reformatting the below....

OK. Noted. 

> 
That's rather odd. I'm not sure what the deal iw with /casper-rw-backing and /cow. Do you have any filesystems or mount points with those names?

No idea! Never heard of these before. I don't think I ever mounted something as "/cow". LOL

I am system rescue CD right now. The good news is that I can mount sda6, which is where my /home partition is. I still can't mount or scan sda1. 

At this point, I think it's time to cut my losses. It's fast approaching Monday morning and I need my computer back for work. If I could just wipe sda1 and start again, that would be the lesser of two evils. 

Any idea how I could go about a successful fresh install?

---

### Post by Jimmy9pints on 2011-01-16
Sorry. Post got duplicated because the connection is extremely slow to the Ubuntu forums from China at times. 

I got several timeout errors before the post was successful.

---

### Post by Jimmy9pints on 2011-01-16
sorry. Duplicate post.

---

### Post by Jimmy9pints on 2011-01-16
duplicate post.

---

### Post by amsterdamharu on 2011-01-16
For most disk tools the partition has to be unmounted so reformating isn't an option right now.

You could try tinycore linux (only 10MB) and unetbootin to stick it on a usb and boot off that. If you have a cable connection you can use the program browser and click connect to install fsck

If you already accepted loss of data you could do an fsck on sda1 instead of dd and do a check on the dd.

By the way; tinycore usually has hda1. You can check your harddisks with:
```
sudo fdisk -l
```
to see how it's interpreted.

The tools you need to download and install may have the name fstools, the command would be:
```
sudo fsck.ext? /dev/hda1
```

Not sure what the filesystem type of sda1 is so you should change ext? with ext3 or ext4

I am in China as well (not so tropical Hainan) so will be going to bed now, hope it works out.

---

### Post by amsterdamharu on 2011-01-16
I just checked with tinycore in virtualbox and there is no need to install anything. Just open a terminal after you get the tinycore desktop and type the following command

```
sudo fsck /dev/hda1
```

---

### Post by srs5694 on 2011-01-16
If you can mount /home, and if you have enough free space on it, you could try the dd trick to create an image file of /dev/sda1 on /home. (Don't worry about the ongoing access to /dev/sda1 for the moment.) Try e2fsck on it, and try mounting it with the loopback driver:

```

mount -o loop /mnt/wherever-home-is/sda1.img /mnt/anothermountpoint

```

If you can read the image file, you can then delete /dev/sda1 with fdisk (see below), reboot, create a new /dev/sda1 of the *exact same size*, and restore the image with dd.

You can easily delete any partition with fdisk, whether or not it's currently in use. You can do this as part of the just-outlined recovery procedure, or as a last-ditch effort to reinstall Ubuntu while preserving your /home partition. Type "fdisk -u /dev/sda" (prepend "sudo" if you're doing this from an Ubuntu live CD), type "p" to view the partition table (write down the start and end sector numbers of the partition you intend to delete), type "d" to delete a partition (you'll be prompted for a partition number), type "p" to verify you deleted the correct partition, and then type "w" to save your changes. When you reboot, there's no way that the computer can attempt to use that partition, since it won't exist. You can then use fdisk to re-create the partition. Use the "n" option to do this. If you plan to restore an image, be sure to create a partition with the exact same start and end sector numbers as you used originally. (This means you must launch fdisk with the "-u" option both times, so that you see and enter values in sectors rather than in cylinders.)

Oooh.... I just had an idea! Before you try to re-install Ubuntu, if you re-create the partition in this way, it's conceivable that whatever's trying to access the partition won't be able to do so immediately after you've re-created it and before you reboot. Thus, you might try e2fsck at this point, just for the heck of it. You might luck out and get it to fix the problem. If not, go ahead and use mkfs to create a new filesystem on the partition and re-install Ubuntu.

---

### Post by Jimmy9pints on 2011-01-17
Cool. Stage 1 seems to have worked. 

```
root@sysresccd /mnt/sda6temp/root_backup % e2fsck -p image.img
image.img: clean, 191835/1222992 files, 1021853/4882432 blocks
root@sysresccd /mnt/sda6temp/root_backup % ls /mnt 
backup  cdrom  custom  floppy  gentoo  sda1image  sda6temp  windows
root@sysresccd /mnt/sda6temp/root_backup % mount -o loop /mnt/sda6temp/root_backup/image.img /mnt/sda1image 
root@sysresccd /mnt/sda6temp/root_backup % ls /mnt/sda1image 
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old 
```

fdisk

```
root@sysresccd /mnt/sda6temp/root_backup % fdisk -u /dev/sda

Command (m for help): p

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x561f8bbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2        39065598   488394751   224664577    5  Extended
/dev/sda5        39065600    43063295     1998848   82  Linux swap / Solaris
/dev/sda6        43065344   488394751   222664704   83  Linux
```

The next stage is using option d to delete the partition. 

I didn't copy paste the code for this part (sorry) but for those of you who are interested, the syntax is:

```
Command (m for help): d
Partition number (1-9): 1
```

Then you need to press w to save and exit. 

It reports the partition table has been changed. 

Then I did the following:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x561f8bbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        39065598   488394751   224664577    5  Extended
/dev/sda5        39065600    43063295     1998848   82  Linux swap / Solaris
/dev/sda6        43065344   488394751   222664704   83  Linux

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Partition number (1-4, default 1): 1
First sector (2048-488397167, default 2048): 2048
Last sector, +sectors or +size{K,M,G} (2048-39065597, default 39065597): 39063551

Command (m for help): p

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x561f8bbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    39063551    19530752   83  Linux
/dev/sda2        39065598   488394751   224664577    5  Extended
/dev/sda5        39065600    43063295     1998848   82  Linux swap / Solaris
/dev/sda6        43065344   488394751   222664704   83  Linux
```

And the last stage:

```
root@sysresccd /root % dd if=/mnt/sda6temp/root_backup/image.img of=/dev/sda1
39061504+0 records in
39061504+0 records out
19999490048 bytes (20 GB) copied, 2664.37 s, 7.5 MB/s
```

---

### Post by Jenkev3 on 2011-01-17
I too have a similar problem. There is a Caviar hd here from an Imac - there was a power outage - so the owner replaced it with a new drive. However, I have been trying to recover any data from this old drive- The imac didn't even recognise the hd. So I connected it to an asus which only operating system I'm using for it is Ubuntu- I ran test disk.. it recognises the HD after I connected it via usb. . . . My question is how do I get the data into the computer if there is any that isn't corrupt- i'm having a hard time figuring this out. - I'm new to forums so please excuse me if I wrote this question in the wrong area... thanks! 
Jen

---

### Post by Jimmy9pints on 2011-01-17
OK following all of my steps in the previous post, everything looked as if it was going smoothly. 

to recap: I'd fixed the .img file using e2fsck, mounted it to check it (it seemed fine), then deleted the old sda1 partition, created a new clean one of the exact same size, saved the changes, then used dd to restore the image to the new partition. 

However, when I restarted, grub reported "no such partition". I am back in System rescue disk and fdisk indeed reports that the partition's not there. 

```
root@sysresccd /root % fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x561f8bbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        39065598   488394751   224664577    5  Extended
/dev/sda5        39065600    43063295     1998848   82  Linux swap / Solaris
/dev/sda6        43065344   488394751   222664704   83  Linux
```


What did I do wrong?

---

### Post by amsterdamharu on 2011-01-17
sda1 was your Linux system partition so I guess you can mount the image and copy the files:

```
sudo mount -t ext4 -o loop myimgage.img /mnt
```

re create sda1 partition and mount it in /media/sda1
```
sudo mkdir -p /media/sda1
sudo mount /dev/sda1 /media/sda1
sudo cp -R /mnt/* /media/sda1/
```Now you might be missing grub in sda1 but you can start from live CD and then re install grub.

---

### Post by Jimmy9pints on 2011-01-17
SUCCESS!

Thanks again for your input. 

But I back tracked over my steps. I think I forgot to save changes after creating the new partition. 

Anyway, by repeating the steps I managed to do it. 

I am now happily writing this from my fully restored Ubuntu installation without any data loss!

Big thank you to all people that helped me sort out this problem. The community is really what makes Ubuntu worth while.

---

### Post by Jimmy9pints on 2011-02-11
Just a few weeks later and here I am again tracing over my steps to fix the same problem...but this time on a different computer (my wife's). 

Exactly the same symptoms. Cause was hard resetting the computer because it had frozen up apparently. 

What could be causing this problem to occur so easily in the Ubuntu system?

---

### Post by Jimmy9pints on 2011-02-11
So, I was going through the same routine again - I thought, since I was fairly practised at this it would be straight forward, but after making the backup of sda1 over to sda7 using dd, I wasn't able to run e2fsck on the img file successfully.

Here's the output of that:
```
ubuntu@ubuntu:/mnt/sda7temp$ sudo e2fsck sda1.img e2fsck 1.41.12 (17-May-2010)
Error reading block 2129920 (Invalid argument).  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 2129920 (Invalid argument).  Ignore error<y>? yes

Superblock has an invalid journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Superblock has_journal flag is clear, but a journal inode is present.
Clear<y>? yes

The filesystem size (according to the superblock) is 4292352 blocks
The physical size of the device is 1048575 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

Error writing block 2129920 (Invalid argument).  Ignore error<y>? yes 
```


That didn't fix it because when I try to mount it I get:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop2,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so 
```

Where do I go from here? debugfs ?


Any help would be very much appreciated before my wife starts telling me to just install windows!

Thanks!

Jimmy

---

### Post by Jimmy9pints on 2011-02-12
Oh dear! 

This problem is big and significantly different enough from the last one to warrant [a new thread]("http://ubuntuforums.org/showthread.php?p=10451912#post10451912").

Boooooooooooh!  ](*,)

---

### Post by kumarnarain on 2011-05-15
Hai
Can you post a detailed step by step detail..I am not still very comfortable with a CLI.....I am getting the same scenario after a power  outage induced reboot...
Kumar

---

### Post by rmhartman on 2011-05-20
Having the same problem as described here.  Will be trying System Rescue CD on Monday ... but if anyone else has any other ideas on how to fix this I would like to hear them, just in case System Rescue CD fails to give us access to the locked partition ...

---

### Post by Jimmy9pints on 2011-05-23
A few people are having the same problems here so I'll help if I can, though, it's been quite a few months, so I'll do my best to remember. 

I  am not exactly sure of the nature of the problem with the disk, but what I needed to do was run "e2fsck" on it. My initial method to do that was to get a live USB and simply run that on the unmounted disk. It didn't work because something was keeping the disk busy. 

The only way to do it was to make an image of the disk, and run e2fsck on that. Then, when it had done its work, correcting all the errors, copy that back. 

If the disk is not broken, i.e. it's just a file system problem, then the tool used for making the image is dd. If the disk itself is damaged and/or you have I/O errors, you'll need ddrescue. In each case, you'll need to make the image on a disk or partition that is not damaged and that has enough space to fit the image. 

Then once you have the image, you can run e2fsck on it and restore the fixed image to the right place. Everything should run fine. 

**So to go over the method again:**
[LIST]
[*]Make an image of the damaged partition
[*]Run e2fsck on the image
[*]Restore the fixed image to the right place
[/LIST]

**More Detailed Instructions**

(N.B. My command line skills are not the best, so if anybody spots any errors, please point them out).

Firstly, get yourself a copy of something like "system rescue disk" or Ubuntu rescue remix. 

Then, from your terminal, mount whatever is going to receive the data:

```
sudo mkdir /mount/myExternal
sudo mount /dev/sde/ /mount/myExternal
```

```
sudo dd if=/dev/sde of=/mount/myExternal/image.dd
```
Where sde  is the name of  the disk with problems and "if" means input file, "of" means output file, and the path is a mounted external disk.

In my case, once I used an external USB (when the disk was dying) and once I used an empty partition on the same disk (when the only problem was some file system corruption).

More advice  from [DGortze380]("http://ubuntuforums.org/showpost.php?p=7575314&postcount=7"): "use just /dev/sde to copy the whole drive, including partition informations. /dev/sde1 would only copy the first partition and is not what you want.

And while I'm at it ... image.dd is simply a file name, call it whatever you like. .dd is an extension commonly used in forensics for this type of image, but shouldn't matter much in this case."

In the case of the ddrescue, if you have system rescue disk or some  other similar distro, it should be installed. Make sure you are using the right program though. Beware:

"The gddrescue package provides /sbin/ddrescue.
The ddrescue package provides /bin/dd_rescue.

ddrescue and dd_rescue are different programs, which do similar things. That gddrescue provides a program with the same name as an unrelated package makes for some confusion."  (advice from [unutbu]("http://ubuntuforums.org/showpost.php?p=7575733&postcount=10")).

Issue a command like this:
```
sudo ddrescue --no-split /dev/sde /mount/myExternal/image.dd /mount/myExternal/logfile
```
then
```
sudo ddrescue --direct --max-retries=3 /dev/sde /mount/myExternal/image.dd /mount/myExternal/logfile
```
Note, ddrescue requires a logfile so it can resume operations if it's interrupted. 

Creating the image will take quite some time. The length will depend on the amount of data and (in the case of a damaged disk) the extent of  the damage. From memory, for dd to copy 20G of data it took an hour or two. For ddrescue to pull over 20GB data from a damaged disk it took about 4-5days!!! 

Once the data is on the external disk, you can  proceed with the check and repair using e2fsck.

```
sudo e2fsck -n -f -v /mount/myExternal/image.dd
```

It should check, find errors, and repair. 

Then, you can  move on to restore the image to the original partition, or in the case of a broken disk, to your new hard drive.

```
sudo dd if=/mount/myExternal/image.dd of=/dev/sde
```

And you should be done. 

(Other community members please check for errors.)


People with problems, please ask questions.

---

### Post by Slopwith on 2011-06-12
Hi All. I believe Noob is the correct phrase for me. I have long been dallying with the idea of Linux-I had a little play a couple of years ago with Linspire/Freespire but just a play but it was enough to start piquing my interest. Apples are out of my financial league and I have become increasingly frustrated with MS. My little EeePC seems to take about ten minutes before it is usuable-(even after removing Anti-virus) and whenever I try and do someting it seems to be clunking away doing something so I started coming back to looking at Linux. I loaded Netbook remix as a dual boot on the EeePC which was OK and then upgraded to the newstyle with the unity type interface but could not work out how to see my Windows partitions and My Documents so upgraded to the full 10.10 which is working well. I was so encouraged by this that I set upp 10.10 on a separate drive on my desktop and also, while a friend who is Linux savvy was visiting, set up Mythbuntu on a dedicated box with a seperate drive that had all my movies (fortunately my friend was here as I do not think I would have manged the Mythbuntu setup). All was well and I was starting to explore.
I should add at this point that I live in Abu Dhabi in the UAE. Some work had been done on my property and obviously not very well so the power tripped in my villa several times. Both the desktop Ubuntu 10.10 and the Mythbuntu are now no longer booting. The desktop which I am now of course using via Windows still has Grub with the option of selecting Ubuntu but select it and nothing much happens. Mythbuntu comes up with some stuff about busy box. I have loaded a live CD on the Myth system and doing some of the bits on this posting can see my hard drive sda with various partitions including sda1. However, my point is and maybe I should send this post direct to Cananonical, most of the stuff in this post is beyond me. I thought Uninterruptable power supplies were so you didn't lose data-I did not think I would have to buy one for every PC to save the actual operating system! I am really quite disapointed that Ubuntu has proved to be so susceptible to power failures. It may be robust in other areas but this is leaving me lost. The desktop is not really an issue as I can start agin-do I want to now but the Myth required a lot of work by my friend to get running and I won't be doing a re-install on that one. 
In short, I hope administrators can pass on a message to Cananonical that there needs to be some sort of recovery routine in place.
Thank you. I just hate wasting time on computers. God I wish I could afford a Mac!
Also a big thank you to the posters on this thread-I will try what I can following it to recover the Myth system.

---

