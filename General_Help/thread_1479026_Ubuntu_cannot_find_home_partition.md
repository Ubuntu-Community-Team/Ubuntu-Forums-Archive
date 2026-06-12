---
title: "Ubuntu cannot find home partition"
date: 2010-05-10
forum: General Help
---

### Post by obaid on 2010-05-10
Hi ubuntu community.

last day i installed windows 7 on free space "unallocated space" of my hard drive. and fixed the grub to dual boot ubuntu and win7.

in grub menu i select to start ubuntu, during the boot splash screen, it gives a message down that /home partition could not be mounted.

my /home partition is encrypted (during ubuntu setup from live CD, i chose to make it encrypted)

Here is a screenshot of Gparted when i first start it:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156319&stc=1&d=1273501735[/IMG]

/etc/fstab says that during ubuntu installation home partition was on /dev/sda6, but Gparted shows that it is unallocated (3rd partition from right)

i tried my best to search and fix it, but couldn't.

all the solutions i find in internet says that first i have to mount the encrypted home partition and then follows other steps, but in my case i cannot even mount it because it doesn't exist.

i have learned my lesson :-) "Backup important files before playing with OS"
i have important emails in my home dir and some other files, if someone could help i would appreciate.

Question: is it possible that windows 7 installer resized my /home partition in /dev/sda6, because i remember it was 80 GiB not 76 GiB ???

---

### Post by obaid on 2010-05-10
Up

---

### Post by obaid on 2010-05-11
Up

---

### Post by dandnsmith on 2010-05-11
I don't understand what is going on here
1. Win7 likes partitions on different boundaries, with a larger blocksize - if you allowed it to mess with the partition table during installation post Ubuntu, I'm not sure what would happen.

2. I don't like the look of all those unallocated spaces - has something been deleted after partitioning? I'd expect to see a partition number, even if gparted thought it was wrongly laid out.

3. A look at the partitioning with 'fdisk -l /dev/sda' might help by showing more detail - I've had gparted quirks (have you the latest version?, as I see you're talking UBuntu9.10)

---

### Post by obaid on 2010-05-11
i intentionaly left all this free space.
before i install win7, i allocated 80 gb ntfs partition for it from ubuntu, during win7 installation i just selected that drive.

once installation completed, ubuntu wont boot saying that my home partition cannot be mounted.

in Gparted, after /dev/sda3 you see 76 GiB unallocated space, that was my home partition /dev/sda6, but now it just disappeared showing unallocated space.

---

### Post by srs5694 on 2010-05-11
Some suggestions:


[list=1]
[*]If possible, *before you try anything else,* make a complete backup of the disk to another disk. You can use dd for this, as in "sudo dd if=/dev/sda of=/dev/sdb". This copies /dev/sda to /dev/sdb. (*Be sure* to get the if= and of= options right; if you get them wrong, you'll wipe out the original or wipe out some other disk! /dev/sdb must be a blank (or unused) disk; change it to /dev/sdc, /dev/sdd, or whatever if you've got a /dev/sdb that's in use.) It will probably take hours to complete. This step is insurance against making matters worse; if you do further damage to the disk, you'll have something to fall back on.
[*]You can use the [testdisk](http://www.cgsecurity.org/wiki/TestDisk) program to locate lost partitions. It's not 100% reliable, but it might do the job.
[*]You may be able to use fdisk to recreate your lost partition. Type "sudo fdisk /dev/sda", then use the "n" option to create a new logical partition. Make it fill the current extended partition. When you're done, reboot and see if you can mount it. This will work *if* your original /home partition started at the very start of the extended partition *and if* that extended partition start point has not changed. The last of those *if*s may not be valid; it's conceivable that your partition was lost because Windows changed the start of the extended partition and then fumbled the relocation of that first logical partition's start point.
[/list]


Good luck!

---

### Post by dandnsmith on 2010-05-11
> **srs5694 said:**
> If possible, *before you try anything else,* make a complete backup of the disk to another disk. You can use dd for this, as in "sudo dd if=/dev/sda of=/dev/sdb". This copies /dev/sda to /dev/sdb.

Using this command is, or can be dangerous, as it will force the size, partition parameters and everything onto the copy - it's only OK if using a disk which is the same model as the original (so taking care of size and geometry).

---

