---
title: "Damaged OS"
date: 2009-07-11
forum: General Help
---

### Post by henrywm on 2009-07-11
Something has gone wrong in my system. 

I am running a dual boot with Windows XP MCE and Ubuntu 9.04.

I was forced to do a hard shutdown. Windows still works fine, but when I boot into Ubuntu it loads GRUB4DOS and gives me a GRUB command line.

TAB lists possible commands

Escape gives me a menu:
find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /grub.menu/lst
commandline
reboot
halt

None of these options let me boot into a GUI. Any ideas?

---

### Post by HermanAB on 2009-07-11
Howdy,

You have to boot with an Ubuntu CD, then run fsck.ext3 manually.

---

### Post by yeaitsdark on 2009-07-11
It's a little bit difficult to direct you to a solution with limited information. My pure guess is that you might have been updating the system at the time, and it doesn't have the right path in grub for your Ubuntu installation. Maybe it simply didn't write the new menu.lst or the new kernel.

Is grub your main boot loader, or does the Windows boot loader chain into grub?

I presume that you might benefit from this tutorial:
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS)

As you can do this from Windows. You may choose to do it from the live CD and install grub that way. In which case this will be helpful to you.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)



Best of luck.

Try HermanAB's first, as yea it could just be the filesystem.

---

### Post by henrywm on 2009-07-11
yeaitsdark:

I was not running an update. I was running Super Tux Kart. It froze. The computer did not really freeze, but everything was very slow, and I was unable to close the program.

I do not know what the main loader is. The system had Windows first. I then installed Ubuntu with the installer at wubi-installer.org.

Does that give you enough information?

I am downloading a disk image for a live CD so that I can try HermanAB's suggestion. I did not have a live CD because I did not need one with the wubi-installer.org program.

---

### Post by yeaitsdark on 2009-07-11
Yes that changes things for sure. Good information that, because of the way the Wubi installer works is different than most Live CD installations.

I recommend you view this page:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

More specifically the part involving this:

> 
How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:
```
sudo mkdir /win
sudo mount /dev/sda1 /win

```
> 
Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```
> 

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:

```

sudo fsck /win/ubuntu/disks/root.disk

```

You could of course simply reinstall via Wubi, but I presume you'd like to keep the installation. This should fix this problem.

---

### Post by henrywm on 2009-07-12
I tried four Ubuntu disks. The computer will not boot with them, but it will boot with my Windows restore disk.

---

### Post by henrywm on 2009-07-12
I will try to install DSL with Syslinux to a USB stick tomorrow and boot with that and then run the commands you suggested. If that does not work, is there any option other than reinstalling the wubi installation?

---

### Post by henrywm on 2009-07-12
I decided to try tonight instead of waiting. It did not work. Here are the results:

sudo mount /dev/sda1 /win
   could not mount (already mounted or /win busy)

sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
   no such file or directory

fsck just displayed the help for the fsck command

---

### Post by yeaitsdark on 2009-07-12
> **henrywm said:**
> 
sudo mount /dev/sda1 /win
   could not mount (already mounted or /win busy)


Please try to unmount the volume first.

```
sudo umount /dev/sda1
```

It is most likely auto mounting the drive. (which is fine and you could find said directory but for the sake of ease, we'll mount it where we want it)

Then try the rest of the commands. 

If you are unable to unmount this command will show you what files are opened on the drive.

```
lsof /dev/sda1
```

Let me know if that helps. The following commands were only unsuccessful due to the first one's failure.

---

### Post by TeamJ on 2009-07-12
perhaps your HDD is damaged? try removing the partition (leaving th XP one intact), then creating and installing on a new one

---

### Post by henrywm on 2009-07-12
When I ran "sudo umount /dev/sda1" it said "umount: /cdrom: device is busy.
When I ran the lsof command it said "command not found"

---

### Post by henrywm on 2009-07-12
Is there anything else I can do to fix it?

---

### Post by itsjareds on 2009-07-12
Are you shutting down correctly in Windows? I had a problem similar to this when I used a Wubi boot, and that's why I've switched to a physical partition. My problem was actually that my Windows computer would restart without warning, and apparently the Windows filesystem still shows as busy to the computer. This is a problem with Wubi users because your Ubuntu install is actually a part of Windows FS. My only difference is that my computer booted into a busybox shell, and I didn't know what to do from there. I'm thinking that your problem may be along the same lines, though.

Try shutting down safely, or boot into Windows safe mode with command line and then rebooting with the command:
> shutdown -s -f -t 00
Then reboot and try to boot Ubuntu.

---

### Post by henrywm on 2009-07-12
I am closing Windows correctly. The problem started after I was forced to do a hard shutdown in Ubuntu.

I tried that command and then tried to boot into Ubuntu. It did not help.


Can I do a physical partition install on a system which already has Windows without removing Windows?

---

### Post by itsjareds on 2009-07-12
Yep, that's what I've done. This is the magic of partitioning :). When you go to install Ubuntu again through the LiveCD, there is a partitioning tool. Follow the instructions on Ubuntu's [HowToPartition]("https://help.ubuntu.com/community/HowtoPartition").

Just be VERY careful when you do this, I would recommend that you do not move or resize a partition from the left side. I once moved my Windows 7 partition over a few megabytes, and ended up corrupting a system file and couldn't boot into it. So if you're going to be resizing your Windows partition, be safe(r) and do it from the right side towards the left.

If you get an error about not being able to resize the partition, it's probably because there are some files at the end of your hard disk. This is normal with a Windows disk. To overcome this, you have to defragment your Windows partition to move all the data to the very right of the partition, so that you can resize it.

The best defragmenter I have found that also will consolidate your free space (which means move your data to the front of the hard drive) is PerfectDisk.

Here's a download, it's a free trial:
[http://www.perfectdisk.com/products/home-perfectdisk10-home-edition/learn-more]("http://www.perfectdisk.com/products/home-perfectdisk10-home-edition/learn-more")

Good luck, post back if you need more help

---

### Post by henrywm on 2009-07-12
This computer fails when  try to burn CDs, and it will not read CDs burned by my other computer. In both cases I get a clicking sound. I guess I will need to order a CD.

---

### Post by itsjareds on 2009-07-12
Another idea is to write the LiveCD to a USB flash drive (must have enough space for the CD image). Here's a program that will do it for you:

[UNetbootin]("http://unetbootin.sourceforge.net/")

You'll need to format the flash drive to FAT16.

---

### Post by henrywm on 2009-07-13
I installed PerfectDisk. Is there a way to consolidate the space between the MFT Zone and the rest of the files?

---

### Post by henrywm on 2009-07-13
[This]("https://help.ubuntu.com/community/Partitioning%20issues") says to make partitions only from within Windows. Does that also apply when using the partitioner in the live CD installer

---

### Post by itsjareds on 2009-07-13
> **henrywm said:**
> I installed PerfectDisk. Is there a way to consolidate the space between the MFT Zone and the rest of the files?

Yep, there should be a button at the top that says "Defragment System Files". This will include all those files that were unmovable before.

Oh, and I forgot to say this, but disable your paging file before you defragment and until you resize the partition. Your paging file usually resides at the very end of the partition, making it hard to defragment. You can put it back after you've resized it.

---
edit: I didn't know about only partitioning from Windows. I did all of my partitioning from the GParted LiveCD and have not had a problem. (this included creating an ext3 partition, resizing 2 NTFS partitions, and creating a logical partition for swap.

---

### Post by henrywm on 2009-07-13
It says those files are in use. What happens if I force the program to free them?

---

### Post by itsjareds on 2009-07-13
There should be an option to schedule a defrag for system files on the next reboot, that's what I did. When you boot next into Windows, it'll stop at the login screen and do some command prompt-type stuff. Looks similar to the Windows updater and chkdsk.

---

### Post by henrywm on 2009-07-13
How do you disable the paging file?
The partitioning instructions on the Ubuntu site appear to be based on an older version.

---

### Post by itsjareds on 2009-07-13
Disabling the paging file should be done in Windows. Are you using Vista or XP?

I only know XP, so try to bear with me if you have Vista:

Go to Start > Control Panel > System, then go to the Advanced tab. Under Performance, click Settings. Click the Advanced tab again. Under Virtual Memory, click "No paging file".

Then do a defrag of both regular and system files (sys files upon reboot), both with consolidate free space.

---

### Post by henrywm on 2009-07-13
I removed the wubi install before i defragged, but Ubuntu still appears in the boot list. How do I remove it? Will it be fine to leave it and let the live cd install remove it?

---

### Post by itsjareds on 2009-07-13
To remove it, go on Windows and find C:/boot.ini. Open it with Notepad and remove the entry for Ubuntu.

It should look like this:

```
C:\grldr="Ubuntu"
```

There may be other lines that are related to Ubuntu, just delete those as well. If you try to boot into Ubuntu again it'll say missing bootloader.

---

### Post by raymondh on 2009-07-13
For reference

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by henrywm on 2009-07-15
The partitioning instructions on the Ubuntu site appear to be based on an older version. How should I partition with the new version?

---

### Post by itsjareds on 2009-07-15
I would be safe and use Windows tools to **create** a partition. Format it to NTFS or FAT32 or anything (it will be reformatted). Apparently it's safer to create partitions using the Windows partitioner when there are NTFS partitions, but safer to reformat using Linux tools.

So create the partition in Windows, then run the Ubuntu LiveCD and select the extra partition you created. Reformat it to ext3 and select it for installation and you should be set.

---

