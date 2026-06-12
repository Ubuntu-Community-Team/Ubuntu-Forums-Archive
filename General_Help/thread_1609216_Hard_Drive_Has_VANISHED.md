---
title: "Hard Drive Has VANISHED"
date: 2010-10-30
forum: General Help
---

### Post by SteveQuinn on 2010-10-30
Ok so heres what happened yesterday.

After using 10.04LTS I decided to upgrade to 10.10 as I was happy with Ubuntu..

In "My Computer" which I get to via Vista I had the following:

OS C:\
D:\ which is where I installed Ubuntu

and below them the HP Recovery thing which I assume is a partition of the c:\ drive.

Anyway after I updated to 10.10 I do not get a choice of where to boot to and now in "My Computer" I am greeted with OS C:\ and HP_Recovery D:\

Also if I go into Device manager 2 hard drives show up but it doesnt have anything in its Volume when I click populate unlike the other hard drive that says OS and Recovery etc.

So I am confused - whats gone wrong and how do I fix it?

---

### Post by oneNF on 2010-10-30
question. can you still boot into Ubuntu? 

I haven't dual booted for a while but recollect that ext3 type disk format can't be read by windows.  I would guess that if you can still boot Ubuntu, windows just can't recognise the partition in ext format.
cheers

---

### Post by wilee-nilee on 2010-10-30
Sounds like a wubi install run the boot script in my signature and post the text in code tags. You can generate code tags in the reply window by clicking on the (#) then put the text between.

---

### Post by SteveQuinn on 2010-10-31
Ok I couldnt log into Ubuntu at all, like I said the drive had vanished.

Someone suggested going into Computer Management, then Disk Management and it was there, so I deleted the partition and the drive and formatted it. Now it shows again.

10.04 was via 'wubi' and I upgraded to 10.10 via update manager, should I have done it a different way?

Also can 10.10 be ran and installed via a pendrive/flashdrive?

---

### Post by efflandt on 2010-10-31
A wubi upgrade can be risky.  So If you have been using Ubuntu long enough to want to upgrade it is probably time to do a normal install to its own partition, instead of within Windows.

10.10 can be run from USB, either as a bootable liveinstall iso on as little as 1 GB flash (FAT32 formatted), or regular install if you have enough room (8 GB or larger recommended).

However, syslinux changed, so if you try to do the live/install iso on USB with a tool that is too old, it may not work.  But you could do it from live/install CD as long as you have access to the iso file (even if on a Windows drive) on that computer.  The live/install iso is not very secure because it auto logs on as default user ubuntu who can do pretty much anything as root using sudo with no password.  Startup Disk Creator for doing the bootable iso has a slider for persistent data if you want to save settings (for wireless, timezone, etc.) or to add programs, but do not do any kernel updates, because that is on a compressed (squashfs) filesystem that boots before any persistent data that you did is mounted.

If you do a "regular" install to USB you just have to pay attention in the manual partitioning part of install, at the bottom of that page, to put grub in the mbr of the USB drive.  Once installed, it is a regular system, so you can add programs, do updates, etc.  I ran Maverick since it was beta on a USB hard drive and updated that into RC and then release version.

It can be a good idea to run a new version from USB just to make sure that you have no issues, or to resolve them before messing up your existing system.

---

### Post by SteveQuinn on 2010-11-04
Ok so in order to do an install to its own drive how do I go about that?

Is it straight forward as I do not want to install over my C:\ I have, as mentioned above, a seperate internal hard drive I would like to use.

---

### Post by oldfred on 2010-11-04
How many partitions do you have? Win7 often uses 2, boot/recovery (hidden) and the main install. Vendors add a utility and an image of your drive as purchased to recovery system to as purchased (not true install or repair). You then have used all 4 partitions allowed under MBR/msdos. If that is the case you will have to delete (backup first) a partition. You can usually copy the image to DVD/CDs in case you ever wanted to total erase and recover windows to as purchased. You should also back up everything valuable before any system changes.

From liveCD (sudo may not be required on liveCD?) Is D: really a drive or just a partition. Windows confused the difference.

```
sudo fdisk -lu
```If windows is Vista or win7 you will want to use the windows tools in the MMC to shrink the windows  partition.

Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by Sigma1 on 2010-11-04
I had a similar experience a while back, and here are the notes I made at the time: the solution worked for me.

Found here: [https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

The solution is to use a live-CD to mount the system (or boot from a completely separate installation), mount the failed OS partition(s), and complete the update (or installation) process which has perhaps not completed:

e.g.

sudo -i

# create a target mount point
mkdir /mnt/target

# mount root (sda8 or whatever disk you want to use)
mount /dev/sda8 /mnt/target
# mount boot
mount /dev/sda9 /mnt/target/boot

# into Jaunty
chroot /mnt/target/

# update
dpkg --configure -a

# done
exit

#unmount
umount /mnt/target/boot
umount /mnt/target

Another good command to know in such cases is: sudo update-initramfs -u -k

---

### Post by alphaamanitin on 2010-11-04
> **SteveQuinn said:**
> Ok so heres what happened yesterday.

After using 10.04LTS I decided to upgrade to 10.10 as I was happy with Ubuntu..

In "My Computer" which I get to via Vista I had the following:

OS C:\
D:\ which is where I installed Ubuntu

and below them the HP Recovery thing which I assume is a partition of the c:\ drive.

Anyway after I updated to 10.10 I do not get a choice of where to boot to and now in "My Computer" I am greeted with OS C:\ and HP_Recovery D:\

Also if I go into Device manager 2 hard drives show up but it doesnt have anything in its Volume when I click populate unlike the other hard drive that says OS and Recovery etc.

So I am confused - whats gone wrong and how do I fix it?


Not sure why it won't boot to Ubuntu, but windows will never show a hard drive that is formatted in Linux formats in 'My Computer' and in Device Manager it will show up but as not having anything in it, and in an unknown format (probably Windows thinks it is in raw or no format).  Not sure, but what you should do is as your computer boots up start hitting whatever button it is for your computer that, takes you to Boot Options.  It should list your CD/DVD drive, both hard drives, and maybe removable media (USB) as boot options.  Select the hard drive that had Ubuntu on it and see if it boots up.

[SIZE=5]**[COLOR=Red]Except...[/COLOR]**[/SIZE]

> **SteveQuinn said:**
> Ok I couldnt log into Ubuntu at all, like I said the drive had vanished.

Someone suggested going into Computer Management, then Disk Management  and it was there, so I deleted the partition and the drive and formatted  it. Now it shows again.

10.04 was via 'wubi' and I upgraded to 10.10 via update manager, should I have done it a different way?

Also can 10.10 be ran and installed via a pendrive/flashdrive?

Sounds to me like you deleted the partition and reformatted drive that had Ubuntu on it in Windows, if so you just destroyed your Ubuntu install on that hard drive.  Unless you checked Quick format in windows, windows does a destructive format, not sure you can get your data back.  It shows back up because it went from a format Windows cannot recognize (for 10.04 probably ext4) to a format windows can recoginize, probably FAT32 or NTFS.

AlphaA

---

### Post by Sigma1 on 2010-11-06
I agree with the last post: Windows won't recognize drives that aren't formatted in NTFS or FAT, and so will consider the rest of the disk as unoccupied space, once ubuntu is installed (supposing you format in ext3 etc).
My suggestion was based on the assumption that perhaps your installation process didn't finish. The steps outlined from launchpad allow you to finish off an aborted installation (as I understand it). I needed these, actually, since a pop-up window asking me whether I wanted to replace menu.lst with the new version popped up *behind* an existing status window, and I ended up thinking the computer had frozen and did a hart reboot, thereby interrupting the installation process :(.
If you had any data, then Windows has probably wiped it, in reformatting. Booting from a live-CD and using a powerful command-line data recovery tool like photorec would be my only suggestion if you had anything important you want to try and salvage.

---

### Post by alphaamanitin on 2010-11-06
I have personally completely recovered a hard drive after a partition deletion and reformatting.  I was, however, using GParted to do the reformat which does not do a destructive reformat.  I used the program TestDisk to recover that drive:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I don't think you will be able to recover much though.  I read that recovery from a Window's reformat is not easy.  Also, the more you have turned on that computer and messed around with the drive that had ubuntu on it, the more you damage your chances of recovery.  Good luck.

AlphaA

---

### Post by SteveQuinn on 2010-11-08
I have installed 10.10 successfully. However there is a strange thing happening.

When I ran 10.04 it would ask me if I would like to head to Windows Vista or Ubuntu. Instead I now get 4 options.
Ubuntu and an Ubuntu recovery mode and then a vista and a vista recovery environment.

Why is this?

Other than that everything appears to be functioning properly except it don't play dvd's.:(

---

### Post by Sigma1 on 2010-11-08
Hello,
Well the four options sound normal to me. You should also have a memory test option, too, I would have thought (memtest). I'm not sure what was happening before though!
As for dvd's, that's probably another thread, but I imagine you've tried installing ubuntu-restricted-extras and looking at the Ubuntu help files, which are fairly complete, as I remember.

---

### Post by oldfred on 2010-11-08
The grub OS prober with Vista also seems to reverse them. The recovery is actually the Windows and the one listed as windows is the recovery in grub's menu.

As you get kernel updates you will also get each new kernel listed. You shuold always keep one old one just in case the newest has issues with your system. You can delete old kernels in synaptic.

---

### Post by SteveQuinn on 2010-11-09
Thanks for the help everyone and yes Fred I did notice they were the wrong way around :)

---

