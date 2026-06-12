---
title: "Replicating WinXP boot on warranty drive"
date: 2010-04-24
forum: General Help
---

### Post by efflandt on 2010-04-24
Just trying to figure out the best way to copy over everything (via Linux) for a warranty replacement of a WinXP boot drive, so everything functions like it does now.  I used chkdsk /f from WinXP in a usb enclosure on another computer to restore WinXP on the defective drive to bootable condition.  But WD Lifeguard confirms the drive has problems that cannot be fixed, so I did advance warranty replacement, and now need to figure out how to copy everything over intact (preferably without locking out what were bad sectors on the old drive).

The computer is an old Dell Inspiron 8200 and the drive is WD 160 GB blue Scorio installed when the original drive failed (XP reinstalled from scratch).  WinXP cannot even recognize a WD Passport on USB.  That may be because it has USB 1.0 ports and XP does not even recognize ports as USB 2.0 on a cardbus card with 2.0 ports.

But due to slow USB ports that do not recognize a USB drive, I would use another computer to copy or clone the drive.  I have seen ntfsclone mentioned (ntfsprog pkg) which looks like a good candidate for copying data, without copying unused space.

But then I need to figure out how to copy over the standard Windows mbr.  I don't have the Dell disks for it now, but could get them if necessary.  Is the mbr simply the first 512 bytes of the drive, and assuming it is sdb, would the following work to snatch a copy?

sudo dd bs=512 count=1 if=/dev/sdb of=mbr.bin

And after swapping, this to copy it to replacement drive?
sudo dd bs=512 count=1 if=mbr.bin of=/dev/sdb

I guess the worst that could happen if I screw up is that I would have to dd zeros to the beginning of the drive and try something else.

---

### Post by utnubuuser on 2010-04-24
Try Clonezilla

---

### Post by oldfred on 2010-04-24
If you need to install a windows boot loader this installs a generic windows boot loader to drive X change X to a or b etc. Does not install lilo but uses it to update MBR. Windows boot loader basically just looks for the active partition (boot flag or *) and jumps to the PBR of that partition to continue booting.

sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

You may still have to run windows repairs:
XP repair disk
[http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip](http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip)
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by dcstar on 2010-04-25
> **efflandt said:**
> 
........
But then I need to figure out how to copy over the standard Windows mbr.  I don't have the Dell disks for it now, but could get them if necessary.  Is the mbr simply the first 512 bytes of the drive, and assuming it is sdb, would the following work to snatch a copy?


The MBR is **not** the first 512 bytes, it is the first 446 bytes. The rest is the primary partition table for that particular drive.

If you want to save the MBR then:
```
dd if=/dev/*hda* of=/mbr-backup bs=446 count=1
```

If you want to copy the MBR to another drive:
```
dd if=/dev/*hda* of=/dev/*hdb* bs=446 count=1
```

Change the drive designations as necessary. gparted can simply copy and paste partitions without requiring additional boot disks.

---

### Post by efflandt on 2010-04-26
Thanks.  I'll try clonezilla first and see how that works.  I have used it to store an image of the old drive on my laptop and will copy that to the warranty drive when I receive it.  I think only about 4K was bad on the defective drive, so if that ends up marked as bad sectors on the cloned filesystem it is no great loss.

I did notice that the mbr file in clonezilla utilities directory is 446 bytes.

I was a little apprehensive because I tried using PING (part image is not ghost) once to image a computer with no system disks, before tampering with it (not sure if former employee took them or our factory has them).  And it made the original hard drive unbootable with a puzzling error "missing or currupt Hal.dll".  Apparently PING did not know how to handle Dell recovery partitions, so it ignored them thinking they would not end up on a restored drive. It also changed boot.ini to boot from sda1 even though it saved the sda2 Windows partition as sda2, and it forgot to change the original boot.ini back to sda2.  Once I figured out the boot.ini issue, I got the existing drive to boot.

That should not be an issue in this case because it only has 1 Windows ntfs partition and an empty ntfs partition where I temporarily had Qimo for kids (based on Ubuntu 8.10) earlier.  And clonezilla seems more refined than PING.  I'll post back if I have any issues after writing the created image to the new drive.

---

### Post by efflandt on 2010-04-30
In the end, clonezilla and ntfsclone did **not** work for copying the partition with bad sectors.  Clonezilla appeared to save the drive image without errors, and restored the empty partition, but failed to restore the partition with bad sectors (ended up empty).

Ntfsclone failed to save the image of the partition with bad sectors, even when using the --rescue switch.  It kept saying to run chkdsk /f from Windows and boot it twice.  But even when doing that once from the command line when it was in a USB enclosure and again when complete check was scheduled from the 2nd boot as internal drive on the original laptop, ntfsclone kept saying that.

I finally downloaded Acronis True Image WD Edition from wdc.com, and that was able to image the bad boot partition.  Since I read that sector by sector cloning can clone bad sectors, I did not do that, and that best way to not have bad sectors locked out on the restored partition was to expand it, I formatted the entire drive as ntfs (instead of 2 partitions) and restored the smaller partition to one big partition.  So the warranty replacement drive now boots and runs XP Pro fine with no errors, like nothing happened.

That still leaves me wondering if there is a Linux solution for replicating a drive with bad sectors that have been locked out (unreadable, but not corrupting current data).

---

