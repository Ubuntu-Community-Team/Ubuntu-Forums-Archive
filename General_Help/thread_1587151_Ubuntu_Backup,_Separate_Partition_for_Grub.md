---
title: "Ubuntu Backup, Separate Partition for Grub"
date: 2010-10-03
forum: General Help
---

### Post by Quarkrad on 2010-10-03
I have found Clonezilla to be one of the best apps for backing up Ubuntu so far, on my dual boot (winxp) desktop.  The problem is the boot sector/grub is not restored when I reinstall and I am left with having to rebuild grub manually.  This has proved to be a pain for me - some methods work sometimes, sometimes not, I find myself frustrated trying to rebuild grub using different methods - it is not consistant.  The theory is not replicated in practical experience.
If I were to put Grub in a separate partition (say sda1) and have Ubuntu in sda2 and winxp in sda3 then if I used Clonezilla to reinstall an image to either sda2 or sda3, when I rebooted would the grub menu still work?  If this is the case then this is the way to go for me.  It has been suggested I backup the whole disk but I have two other (large) storage partitions on HD1 - I would prefer to be able to backup/reinstall just single partitions but not break the whole system (i.e. break the grub boot process).

note.  I backup hd1 to hd2 - two internal disks.

---

### Post by dcstar on 2010-10-03
> **Quarkrad said:**
> I have found Clonezilla to be one of the best apps for backing up Ubuntu so far, on my dual boot (winxp) desktop.  The problem is the boot sector/grub is not restored when I reinstall and I am left with having to rebuild grub manually.
........

Backing up partitions does not back up the MBR - only backing up the whole disk does that.

You may want to try copying the MBR from one disk to another (substitute the **bold** designation for you real disks):

```
#!/bin/sh

dd if=/dev/**hda** of=/dev/**hdb** bs=446 count=1
```

---

### Post by Quackers on 2010-10-03
I have found that to be true too, Quarkrad. I have to re-install grub after restoring a disc image made by Clonezilla. I found it quite amazing that it wouldn't boot, particularly when at the end of the restore procedure Clonezilla states that Grub is being restored (if I remember correctly).
I suspect this may be because I have 2 hard discs and grub is installed in the MBR of both discs. Maybe the restore somehow breaks the link between the 2 grubs?

---

### Post by Quarkrad on 2010-10-03
dcstar - thank you for response.  Sorry - forgot to mention I'm a newbie.  Your suggestion seems to be way to go.  If I reinstall the Ubuntu image and reboot I boot to winxp (because grub2 is broken) - so how would I use your method looking at my winxp Desktop?

---

### Post by dcstar on 2010-10-03
> **Quarkrad said:**
> dcstar - thank you for response.  Sorry - forgot to mention I'm a newbie.  Your suggestion seems to be way to go.  If I reinstall the Ubuntu image and reboot I boot to winxp (because grub2 is broken) - so how would I use your method looking at my winxp Desktop?

Either the Grub MBR or the Windows MBR will be installed on the disk you have designated as the boot device.

If your disk setup remains the same then the original Grub MBR should boot up Grub on the copied Linux partition - but that is not guaranteed and you may still have to go through the proper Grub setup steps.

Keep in mind that the Grub setup sets the boot device to where you install the Grub bootloader.

---

### Post by john newbuntu on 2010-10-03
@dcstar, backing up a partition does back up the MBR and the post-mbr region (at least that is what the message on my screen indicates in newer versions of clonezilla):
[http://clonezilla.org/clonezilla-live/doc/fine-print.php?fullmode=0&path=./01_Save_disk_image/11-saving-disk-image.doc#11-saving-disk-image.doc](http://clonezilla.org/clonezilla-live/doc/fine-print.php?fullmode=0&path=./01_Save_disk_image/11-saving-disk-image.doc#11-saving-disk-image.doc)

Just out of curiosity, choose the expert mode in clonezilla and see if the right options are checked like here(Actually these are the options for cloning entire disk not partitions.):
[http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php](http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php) .  I do not know how the one for image to partition looks like.

The -g and -j2 should be sufficient to reinstall the MBR if those options are present and checked.  I am assuming that it is looking at -g in the image.  If not, it might be a bug or something beyond me.  In any case we will need the MBR and post-MBR region(with the proper core.img) to at least get to the grub rescue prompt.  I feel it is best to do a grub-install as indicated in this post with a liveCD/USB ([http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708))

---

### Post by srs5694 on 2010-10-03
Even backing up the MBR as dcstar suggests isn't always adequate, since GRUB often installs part of itself in the unallocated sectors *after* the MBR, in the boot sector of the Linux boot partition, or even in a dedicated BIOS Boot Partition. (Details vary depending on the partition table type, how GRUB was installed, and what GRUB version was in use.) Some configurations include a pointer to a specific sector number, which might change if you back up and then restore the system.

Unfortunately, I know of no simple and easy backup solution that guarantees getting everything to boot correctly upon a restore to a fresh disk. The best solution I know of is to obtain [Super GRUB Disk,](http://www.supergrubdisk.org) test it with your current working setup to be sure you understand it, use it to boot a newly-restored system, and then re-install GRUB once you've booted a newly-restored system.

FWIW, this problem is largely a consequence of the way the BIOS boots the system, in conjunction with the haphazard way in which boot loaders have evolved over the years. In theory, the new Extensible Firmware Interface (EFI) should do better, since it doesn't rely on boot loader code in the MBR; instead, it uses boot modules stored as regular files in a partition. In practice, I don't know if EFI-based systems really work any better.

---

