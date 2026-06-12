---
title: "Partitions"
date: 2010-09-03
forum: General Help
---

### Post by FinalShot on 2010-09-03
I currently have ubuntu, swap, win7 on their own partitions, and 100gb unallocated. I plan to use it for media, and format it using NTFS as ubuntu and windows reads it. But apparently I have to many primary partitions, I've been trying to change some to logical but that failed. And even if I could, I don't know which ones to change to logical, I assume ubuntu and windows need primary, I'm no sure about linux swap.

Current Partitions:
[img]http://img507.imageshack.us/img507/1846/gpt.png[/img]

---

### Post by FinalShot on 2010-09-03
Bump.

---

### Post by Autodidact on 2010-09-03
What is your actual question?

You should be able to create a new partition within the unallocated space.
Then simply format it to any file-system you like.

---

### Post by Mark Phelps on 2010-09-03
> **Autodidact said:**
> You should be able to create a new partition within the unallocated space.
Then simply format it to any file-system you like.

Unless I'm misreading the snapshot, the OP already has the maximum number of partitions allowed -- three Primary plus an Extended.

In that case, NO, it is NOT a simple matter of creating a new partition.

The OP already figured that out and is asking us what partition to remove to allow them to create another one.

---

### Post by Mark Phelps on 2010-09-03
If you have something to back off the initial Ext4 partition to, I would do that and then, the following:
1) Expand the Extended partition to the left to fill the unallocated space
2) Allocate a new Ext4 partition inside the Extended to use the unallocated space
3) Copy back the contents of the original Ext4 partition

Problem is, this is going to change the partition number of your Ubuntu partition because it will now have an Ext4 partition preceding it.  You will most probably thus, NOT be able to boot into Ubuntu and would have to boot using a LiveCD and reinstall GRUB from that.

Fortunately, the instructions on how to reinstall GRUB from a LiveCD are contained in the link below, in section 11.2:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by srs5694 on 2010-09-03
First, Mark's suggestion won't work; the extended partition (/dev/sda2) is sandwiched in-between /dev/sda1 and /dev/sda3. Thus, it can't be expanded, at least not without doing something about /dev/sda3 and /dev/sda4. (See below for some suggestions about that.)

I can think of several solutions to this problem; in no particular order:


[list]
[*]Delete /dev/sda3 and /dev/sda4, expand the extended partition /dev/sda2 to cover as much of the free space on the disk as desired, and re-install Windows in the remaining space that you don't dedicate to /dev/sda2. This solution is relatively straightforward and doesn't require much technical skill, but it's tedious and if you've got important data in your Windows installation, you'll have to back it up first. Some Windows OEM installers may make this difficult, since they may not support installation to just part of the hard disk.
[*]Delete /dev/sda1, /dev/sda5, and /dev/sda2 (the Linux installation), move /dev/sda2 and /dev/sda3 all the way to the left of the disk using Windows utilities, and re-install Linux on logical partitions following the Windows installation. This is tedious, moving Windows is a bit risky, and if you've got important data in the Linux installation, you'll have to back it up first.
[*]Use a Windows partitioning tool to move /dev/sda4 and /dev/sda3 all the way to the right of the disk. This will move the unallocated space so that it's adjacent to /dev/sda2 (the extended partition), thus enabling you to expand it with GParted. You'll then be able to create more logical partition(s). This process will take a while and it may be risky to Windows, but it's straightforward compared to some of the other options.
[*]Use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert the disk from an MBR format to a GPT, then create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) that includes /dev/sda3 and /dev/sda4. You'll also want to create a [BIOS Boot Partition,](http://grub.enbug.org/BIOS_Boot_Partition) along with any new partition(s) you want. When you're done, you'll need to re-install GRUB. This solution could be relatively simple and quick to implement, provided you do it right; however, there are a number of risks, and hybrid MBRs are ugly and dangerous.
[/list]


You'll need to decide which of these solutions (or others that other people might offer) best suits your needs and skills. If you need more pointers on any of them, feel free to ask and I'll try to provide additional pointers.

---

### Post by WorMzy on 2010-09-03
I'd delete sda2 (and with it, sda5), then create a new extended partition at the end of sda4. A swap partition isn't required for Ubuntu (although having one doesn't hurt) so removing it (temporarily) Is the safest option. Be aware that removing partitions may mess up the way that udev detects disks. sda4 may become sda3, etc. The same holds true for grub, hd3 may become hd2.

---

### Post by FinalShot on 2010-09-03
Thanks for all the suggestions, but they are a little confusing. Currently I plan to install Ubuntu 10.04, Windows 7, and have a media partition. What would the best partition setup from scratch?

---

### Post by FinalShot on 2010-09-03
I'm not sure if I have to have ubuntu or windows as a primary, or the swap for that matter. I'm thinking ubuntu and windows are primary, rest are logical.

---

### Post by srs5694 on 2010-09-03
WorMzy's suggestion is very good; I think it's better than the ones I proposed for most purposes. You could also expand /dev/sda1 to fill the space formerly occupied by /dev/sda2.

It's unlikely that udev would give partitions new device filenames; however, it's conceivable that GParted would do so when it resizes the partitions. Fortunately, recent versions of Ubuntu are pretty robust against such changes, since they use UUIDs (which don't change) rather than partition IDs (which can change) for most purposes.

As to an ideal from-scratch dual-boot Linux/Windows configuration, I'd do this:


[list]
[*]**/dev/sda1** -- Windows C: drive; note just one partition, rather than the two or three used by most Windows OEM installs.
[*]**/dev/sda2** -- Extended partition to fill the rest of the disk; all the subsequent logical partitions are stored within the extended partition.
[*]**/dev/sda5** -- Logical FAT32 or NTFS partition for shared data; used by both Windows (probably as D:) and Linux (mounted wherever you like).
[*]**/dev/sda6** -- Logical root (/) partition for Linux, approximately 10-20GB in size.
[*]**/dev/sda7** -- Logical swap partition for Linux, 1.5-2x the RAM size of the computer.
[*]**/dev/sda8** -- Logical /home partition for Linux.
[/list]


Most of the partitions' sizes depend on your needs. For instance, if you want to share lots of big multimedia files between Linux and Windows, /dev/sda5 should be pretty big; but if you want to store most big files for use only by Linux, /dev/sda5 should be relatively small, and /dev/sda8 should be bigger. You could add partitions if you have particular needs, such as running a mail or Web server under Linux, but few home desktop users need more than I've outlined here.

---

### Post by srs5694 on 2010-09-03
> **FinalShot said:**
> I'm not sure if I have to have ubuntu or windows as a primary, or the swap for that matter. I'm thinking ubuntu and windows are primary, rest are logical.

Windows requires at least one primary partition. Linux does not; you can install Linux on nothing to logical partitions. Doing so preserves your limited supply of primary partitions so that you can use them in the future, should that become necessary. (Unless you lave some unallocated space, you'd still need to delete or resize some partitions, but at least the partition table entries would be available. Converting between primary and logical partition types is non-trivial, so keeping the primary partition table entries free is important.)

---

### Post by FinalShot on 2010-09-03
Thanks a lot, really cleared things up. But why give windows primary? And why have multiple partitions for ubuntu?

---

### Post by FinalShot on 2010-09-03
Oh nevermind, didn't see your last post. Does this look about right to you?

[img]http://img153.imageshack.us/img153/2312/screenshotdevsdagparted.png[/img]

---

### Post by srs5694 on 2010-09-03
Depending on your needs for space, yes, the screen shot in your post #13 looks quite good. Note that, if you intend to re-install Windows, it will wipe GRUB out of the MBR, so it's best to partition, install Windows, and then install Linux. If you install Linux before you install Windows, you'll need to use some variety of emergency disc to re-install GRUB after you install Windows. This really isn't all that hard, but it can be nerve-wracking if you don't know how to deal with it.

---

### Post by FinalShot on 2010-09-03
I've reinstalled Grub over 50 times :)

---

