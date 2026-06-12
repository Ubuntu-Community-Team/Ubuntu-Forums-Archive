---
title: "Restoring GRUB"
date: 2011-07-04
forum: General Help
---

### Post by MetalheadGautham on 2011-07-04
I'm running Ubuntu 9.10 for around 1.5 years.
Need to install windows in my laptop for some stupid course in college which needs windows.
I've emptied a partition for it.
I know that installing windows will forcefully overwrite my MBR.
How do I restore ubuntu's MBR ?

I've the newer version of GRUB...

If this needs a live CD suggest something small I can download...

---

### Post by claracc on 2011-07-04
Here you have the answer: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Herman on 2011-07-04
Yes, I know and there are no Windows installers that will allow you to direct their useless excuse for a MBR to any other partition or drive, unlike the Ubuntu installers.
You are simply forced to accept a MBR for the Windows loader whether you want it or not.

The good news is, you won't need to download anything at all, and all you will need is a blank CD, or a spare USB drive.
If you use a USB drive, you don't need an empty one, even one that already has data in it will do.
It can be formatted with almost any file system, GRUB can even be installed in NTFS.
GRUB won't take up very much room in your USB either.

The following commands are for GRUB2, (the 'new' GRUB).

**To make your very own GRUB2 Rescue CD**, boot into Ubuntu and run either of these two commands, (whichever one works),
(for Karmic Koala and earlier)
```
grub-mkrescue --overlay=/boot/grub GRUB2RESCUE.iso
```( for Lucid Lynx and later),
```
grub-mkrescue --output=rescue.iso /boot/grub
```note: for  the --output=rescue.iso part of the command, you can replace the word 'rescue' with any name you  like for your new .iso file.

Expected Results - 

[LIST=1]
[*]The grub-mkrescue program should make an .iso file in your /home/username directory with your own operating system's GRUB files inside it.
[*]You need to burn the .iso file to a blank CD as an .iso file, not as data, so it will be bootable.
[*]Your GRUB2RESCUE CD should boot to a GNU GRUB Command Line and if you know how to use GRUB in CLI Mode you can do a lot with that, including booting an operating system.
[*]To see your own personalised GRUB Menu and boot in the normal way, just run the command: configfile /grub.cfg
[/LIST]
===================================================================================================================

**GRUB 2 could be very handy in a USB. **You can use it for an emergency boot disk.

      **1. Choose an USB drive** with at least about 60 MiB of space in the partition for grub 2 files, but a little more room than that might be advisable. 
It can be formated with any file system, it doesn't matter if there are already some files in it.
      
      **2. Plug in your USB drive**  while Ubuntu is running, it should be automatically mounted in a few seconds and an icon should appear for it on your desktop.

**3.  Find out what is the real mount point name,** (if you don't already know), this step is important because the actual mount point in /media can have another name than the name you see for the icon on your Desktop.
```
ls /media/
```example output,
> cdrom  cdrom0  VerbatimThe resulting feedback shows that my USB drive's file system is mounted as /media/Verbatim, because it has 'Verbatim' set as the freindly file system label.
If yours comes up as a file system UUID number, I recommend you set your own user freindly file system label to make things easier for yourself now and in the future.
You can do that with GParted in Ubuntu by right-clicking on the partition in the USB drive and selecting 'Label'. or you can use the e2label command, 
```
e2label /dev/sdb1 USBDRIVE 

```Where: Your USB drive is currently called /dev/sdb1 as shown by the blkid command or fdisk, etc,  and where you want to name it 'USBDRIVE', (you can substitute some other name here of your own liking).

**Find out what is the /dev/number** for the file system (or partition),
```
sudo blkid
```example output,
> /dev/sda1: LABEL="ACER" UUID="320D-180E" TYPE="vfat" 
/dev/sda2: LABEL="ACERDATA" UUID="04A6-B8C3" TYPE="vfat" 
/dev/sda5: LABEL="KARMIC" UUID="53640b23-7f97-46a7-b939-b5aedd5097c1" TYPE="ext4" 
/dev/sda6: UUID="88115692-4578-47b5-89ae-dcc3720d95e4" TYPE="swap" 
            /dev/sdb1: LABEL="Verbatim" UUID="1fdc26cf-43ad-40b9-95fa-6d64196513f2" TYPE="reiserfs"Here you can see that the target file system in my USB disk is called 'Verbatim' and it is listed as /dev/sdb1.

**Run grub-install **,
```
sudo grub-install --root-directory=/media/verbatim /dev/sdb
```Where: the mount point is /media/verbatim
Where: The MBR to install GRUB to is /dev/sdb (the USB drive).
NOTE: I didn't install GRUB to /dev/sdb1, because that's the partition boot sector. I need GRUB in the USB disk's MBR, which is called /dev/sdb in this case, since the partition is /dev/sdb1.
      
Watch the thumb drive's LED blink for a few seconds.
      
Now you have a bootable GRUB 2 USB Rescue disk.

But it has no grub.cfg yet so at this stage it will only boot to a command line interface.

To give it a grub.cfg and thus a GRUB Menu, we just need to run grub-mkconfig,
```
sudo grub-mkconfig -o /media/Verbatim/boot/grub/grub.cfg

```===============================================================================================================

Now you can boot up from your BIOS and select your BIOS boot menu and choose the USB drive or CDROM drive if you made a CDROM and boot Ubuntu.

Then re-install GRUB whenver you like when you have Ubuntu running,
```
sudo grub-install /dev/sda


```

---

### Post by Herman on 2011-07-04
Or, if you prefer not to need the use of so many Linux commands, just download [Super Grub Disk]("http://www.supergrubdisk.org/").

---

### Post by MetalheadGautham on 2011-07-04
Is it possible to create such a rescue USB on a FAT partitioned USB drive ?

---

### Post by Herman on 2011-07-05
Yes.
It's a long time since I last tried it but I am pretty sure it will be no problem.
GRUB2 can even work in NTFS, I have tried that not so long ago and it worked fine.

---

