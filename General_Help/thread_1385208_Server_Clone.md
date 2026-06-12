---
title: "Server Clone"
date: 2010-01-19
forum: General Help
---

### Post by tompayne on 2010-01-19
I have an ftp server running ubuntu (7.10) that's been running 24/7 for about 2 years. In fear that it may suddenly give up at some point I want to have an external second hard drive that is constantly cloning the boot disk. I'm a bit new to all this so would really appreciate some advice on the best way to go about this.

Was thinking of using QuickStart but any other suggestions or advice on how to use this would be amazing.

---

### Post by tgalati4 on 2010-01-19
Search in the forums:

cron rsync

---

### Post by wkulecz on 2010-01-19
> **tgalati4 said:**
> Search in the forums:

cron rsync

Yup and have a live CD handy so you can edit /boot/grub/menu.lst, /etc/fstab, and re-install grub. 

Major issues I run into are:  old motherboard had the IDE drives a /dev/hda etc, the replacement finds them as /dev/sda etc.  If the failed drives were mounted/booted by UUID  the clone drive will have a different UUID so it won't work :(

These are pretty easy to fix by booting the liveCD and starting a root terminal window to edit the config files.

--wally.

---

### Post by J V on 2010-01-19
well a full image of the disc would require a cron + dd, but that seems a bit extreme...

Prefer a [Grsync]("apt://grsync")

---

### Post by wkulecz on 2010-01-19
Grsync is a GUI wrapper around rsync, not the best choice for automatic backups.

I have my 6.06 server installed to a (mdadm) raid1 and data on raid 5 with nightly rsync backups to a third and fourth drive.  But I've come to the conclusion that raid is more trouble than its worth as when one of the raid 5 drives failed to start after a short power outage the file system was corrupt after I got it restarted :(   So I had to recover from backups anyways which seemed way easier than rebuilding the array which in this case wasn't possible :(

--wally.

---

### Post by tgalati4 on 2010-01-20
Depending on how critical uptime is, I would simply back up the personal data on an incremental basis (rsync scripts that are run nightly/weekly through cron).  In case of a boot failure, I would simply have a liveCD in the machine as a backup for rescue/boot.  

If the machine really failed (power supply, hard disk, motherboard, etc) then you would have to rebuild the machine anyway.  If just the disk failed, you would have to replace the disk and you would want to put on a newer server edition (such as Hardy).

Six things that are critical for a server:

1.  Decent environment:  temperature, humidity--keep the rain out!
2.  Keep 1' off of the floor--reduces dust pickup.
3.  Annual maintenance--you need to open the box and blow the dust out.  Reseat cables and RAM.  Change the heatsink paste after 5 years.
4.  Personal data backup.
5.  UPS
6.  UPS

---

