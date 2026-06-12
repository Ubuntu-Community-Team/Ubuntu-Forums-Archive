---
title: "Problems mounting a USB Drive from command line"
date: 2011-12-30
forum: General Help
---

### Post by chipbuster on 2011-12-30
Hey guys. I'm almost certain this is an issue of a problem between the keyboard and chair, but I can't figure out for the life of me what I'm doing wrong.

I'm also relatively new to Linux (first installed less than 6 weeks ago).

I'm attempting to mount a USB thumb drive from the command line. To identify what the device is, I first 

> 
$> cd /dev
$> ls > ~/log
Then plug in the USB and

> 
$> ls > ~/log2
$> cd ~
$> diff log log2
This last line spits out two differences:

> 
85a86
> sdb
88a90
> sg3
First off, I'm sure there has to be a better way to do it than this xD. However, I'm fairly certain that the USB drive is sdb. It's formatted in NTFS, so I try to mount it and this happens:

> 
$> sudo mount -t ntfs /dev/sdb /mnt/usb1
Error opening '/dev/sdb': No medium found
Failed to mount '/dev/sdb': No medium found
Now I'm stuck. I'm almost certain that I'm doing something stupidly wrong, but documentation on mount isn't the best, and I don't know what it is. The kicker is that Thunar can see and mount the drive just fine--it lists it as "sdb1." When I unmount it to give that a shot, sdb1 disappears. Is my syntax correct? Can I mount the drive again without having to pull it out and reinsert it? What am I doing wrong here?

I have tried mounting in different directories, with different fstypes, and tried mounting the other difference in devices when the USB is in (sg3). Is there a command that can tell me what device corresponds to what?

---

### Post by dcstar on 2011-12-30
> **chipbuster said:**
> 
..........
Now I'm stuck. I'm almost certain that I'm doing something stupidly wrong, but documentation on mount isn't the best, and I don't know what it is. The kicker is that Thunar can see and mount the drive just fine--it lists it as "sdb1." When I unmount it to give that a shot, sdb1 disappears. Is my syntax correct? Can I mount the drive again without having to pull it out and reinsert it? What am I doing wrong here?

I have tried mounting in different directories, with different fstypes, and tried mounting the other difference in devices when the USB is in (sg3). Is there a command that can tell me what device corresponds to what?

You do not understand the difference between physical devices and the things that they contain.

A drive is a physical device, it can contain (many) partitions. You **cannot** "mount" physical devices, you can only "mount" the partitions (if any) the device contains.

/dev/sdb is a physical device. /dev/sdb1 is a partition within that physical device.

The reason GUI tools like Nautilus and Thunar exist is to automatically manage USB devices and mount removable device partitions, because doing it via the command line is almost insane for novice users.

---

### Post by chipbuster on 2011-12-30
Ahhh, thank you. I knew I was doing something wrong. And would you look at that, mounting sdb1 worked :)

Thanks for clearing that up for me.

---

