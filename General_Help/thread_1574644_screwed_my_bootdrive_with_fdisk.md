---
title: "screwed my bootdrive with fdisk"
date: 2010-09-14
forum: General Help
---

### Post by movies1978 on 2010-09-14
Hi, 
I actually wanted to create partitions on my usbstick, but instead I fdisked new partitions onto my boot + datadrive. It is still running. Is there a chance I can recover that?

best regards movies

---

### Post by bodhi.zazen on 2010-09-14
Stop using the system ASAP.

Boot a live CD and use testdisk. Testdisk is in the ubuntu repos.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by movies1978 on 2010-09-14
thank you for the answer, I will try this out

---

### Post by srs5694 on 2010-09-14
There are at least two possibilities, but both are fairly technical and/or risky:


[list]
[*]Launch fdisk on the problem drive, delete all partitions, and save the changes. Then run [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to have it scan for and recover the old partitions.
[*]For each partition, enter the /sys/block/sda/sda#/ directory (change "sda" to whatever is appropriate, and substitute the partition number for "#"). The start and size files in this directory hold the partition's starting sector number and number of sectors, respectively. Launch fdisk on the drive (using the -u option, as in "sudo fdisk -u /dev/sda"), delete the bogus partitions, and create new partitions using the values obtained in /sys/block/sda/sda# for each partition. You'll need to set partition type codes appropriately. Note that I don't recall how the values are reported for the extended partition, if you've got one (I don't have a system with an extended partition booted at the moment, so I can't check that right now). You might need to create an extended partition using your own judgment of its location and size, after you create the other primary partitions.
[/list]


The first option will work even if you've rebooted, but the second one will work only for as long as Linux remains booted and using the old partition table. The first option relies on TestDisk's ability to recognize filesystems, and it's not guaranteed to produce partition numbering that matches the original. It could fail if there are remnants of old filesystems on the disk (say, if you repartitioned or resized partitions, leaving old data lurking somewhere). The second option should reliably restore your partition table exactly, including partition numbers (but you may need to use your own judgment about boot/active flags and type codes). The second option requires that you make no mistakes when copying the data, and you've got to understand partitioning well enough to create a suitable extended partition for your logical partitions, etc.

Overall, I'd say that the first option is probably best if you're unfamiliar with partitioning minutiae, but the second option (if you've not yet rebooted) may be better if you're comfortable with fdisk and understand distinctions like those between primary, extended, and logical partitions.

Good luck!

---

### Post by srs5694 on 2010-09-14
> **bodhi.zazen said:**
> Stop using the system ASAP.

Actually, continuing to use the system will do no harm, with the caveat that there's a slim chance that a critical filesystem data structure has been damaged. Linux is continuing to use the old partition table, and this partition table *can* be reconstructed -- but only if the system is left running. IMHO, if you're comfortable doing so, as described in my earlier post, it's better to do it that way than to use TestDisk.

> Boot a live CD and use testdisk. Testdisk is in the ubuntu repos.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

As I described in my earlier post to this thread, there is another recovery method that might work better in some situations. Personally, I'd try the /sys method first; however, I understand partitioning well enough to make it work with little risk. Somebody unfamiliar with the relevant tools and data structures might be better off using TestDisk. The risk to doing so, though, is that if there's old data on the disk from previous partitions, TestDisk might get confused and fail completely. That's why I'd recommend using the /sys approach first, if the person is comfortable enough with fdisk to try it.

Oh, one other point: If any logical partitions were created in the accidental partitioning, every filesystem on the disk, or at least those that cover the area just before the logical partitions on the accidentally-created partition scheme, should be checked for errors. For ext2/3/4 filesystems, I'd use "e2fsck -f /dev/sda#" from an emergency boot disc. I'd also recommend re-creating swap space (using "mkswap /dev/sda#" -- be *sure* to get the partition specification right!), then get its UUID number with blkid and edit /etc/fstab appropriately. All of this is advisable because any time a logical partition is created, a special data structure (called an Extended Boot Record, or EBR) is also created *just before* of the logical partition. In the specified situation, the EBR for any bogus logical partition is likely to reside inside some other partition's filesystem. If you're lucky, it will be written to an unallocated sector of the filesystem and it will do no harm. If you're less lucky, it will trash a single file (hopefully something unimportant) or overwrite a filesystem data structure. The filesystem check should locate and (with luck) correct the latter problem. If a file has been damaged, there's not a lot that can be done; it'll just turn up as a damaged file sooner or later.

---

### Post by bodhi.zazen on 2010-09-14
> **srs5694 said:**
> if you're comfortable doing so, as described in my earlier post, it's better to do it that way than to use TestDisk.

There is nothing wrong with your method, and in fact one can simply re-run fdisk to restore the old partition table, assuming they know what they are doing.

The face that the OP has to ask indicated they are not all that experienced and assuming they have valuable data it is probably best to get them on a live CD, IMO, to minimize any further data loss.

---

