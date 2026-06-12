---
title: "partition problem with lvm and primary/extended"
date: 2010-09-09
forum: General Help
---

### Post by darkdragon-001 on 2010-09-09
I somehow messed up my filesystem. I installed Ubuntu directly with LVM. This created an extended partition including a logical one.
When I run out of space, I just increased my space (through VMware) and then added a new PRIMARY partition. Then I added this one to the volumegroup and increased the logical volume. After I did this a few times, there were no longer any primary partitions allowed (only 4). Then I resized the FS, resized the logical volume, resized the volume group, and removed the physical volume. Now I'm no longer able to create an extended volume (only one) but it's not at the end (there are other primary partitions behind this one at the disk), so I'm not able to create some logical volumes.
What is the best possibility to add some space to the LVM and being able to do this a few times in the future again?

further info:
pvscan:
PV /dev/sda5   VG ubuntuserver   lvm2 [199.76 GiB / 0    free]
PV /dev/sda4   VG ubuntuserver   lvm2 [199.99 GiB / 0    free]
Total: 2 [399.75 GiB] / in use: 2 [399.75 GiB] / in no VG: 0 [0]

fdisk -l for sda:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       26109   209463297    5  Extended
/dev/sda4           26109       52216   209710844   83  Linux
/dev/sda5              32       26109   209463296   8e  Linux LVM

There was a /dev/sda3 at the end of the disk. I already deleted this partition.

So the order on the disk is:
sda1 | sda2 (extended) | sda5 (logical referred in sda2) | sda4 | free space

Btw: another question: Does it matter that there is type "Linux" for sda4 or can I without damaging the lvm just change it (with cfdisk) to "Linux LVM"?

---

### Post by srs5694 on 2010-09-09
Your disk has only three primary partitions, so you should be able to create a new /dev/sda3 in the free space at the end of the disk. You might also consider [converting from MBR to GPT](http://www.rodsbooks.com/gdisk/mbr2gpt.html) form, which will enable you to untangle the confusing order of partitions on the disk. Since GPT doesn't make any distinction between primary, extended, and logical partitions this can simplify future partition changes. This will, however, require you to re-install your boot loader, and you should create a small [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) if you use GPT.

If /dev/sda4 contains LVM data, then it's probably best to change its type code in fdisk. If it's working now, then this obviously isn't absolutely necessary, but it's best not to confuse issues with incorrect data.

---

### Post by darkdragon-001 on 2010-09-10
Thanks for your reply. I did all this moving stuff, to free sda3. But when I create a primary partition now, then I'll have the same problem in the future...

Perhaps GPT is a better solution. Is it possible to convert everything, but keeping my LVM structure with the data on it?
I think the bootloader is Grub2. For the boot partition, I think that sda1 is used as such one. It was created by default during install and according to "df" it's mounted on "/boot". Can all this be done with keeping my data and so on?

When I change the type with fdisk, will this have effect on the data on it?

--

I went through some articles (e.g. you links). Just to verify: 
I boot up the system with e.g. an Ubuntu Live. I convert the HDD with "gdisk /dev/sda". Then I reinstall grub with "grub-install /dev/sda". Is this all? Does this not destroy my lvm volume group?

---

### Post by srs5694 on 2010-09-10
> **darkdragon-001 said:**
> Thanks for your reply. I did all this moving stuff, to free sda3. But when I create a primary partition now, then I'll have the same problem in the future...

You could create a new logical partition inside an extended partition. That way, you'll be able to create as many more logical partitions as is necessary, with the caveat that all your logical partitions must reside inside a single contiguous extended partition. Thus, if you were to free space on a part of the disk that had another primary partition between the free space and the extended partition, you'd have to move the primary partition to get the free space next to the extended partition, then expand the extended partition, and then create a new logical partition inside the extended partition.

> Perhaps GPT is a better solution. Is it possible to convert everything, but keeping my LVM structure with the data on it?

Yes, but not with GNU Parted, GParted, or any other libparted-based tool, AFAIK; you'll need to use [GPT fdisk (gdisk).](http://www.rodsbooks.com/gdisk/)

> I think the bootloader is Grub2. For the boot partition, I think that sda1 is used as such one. It was created by default during install and according to "df" it's mounted on "/boot". Can all this be done with keeping my data and so on?

Converting to GPT, if done via GPT fdisk, won't affect where your partition are on the disk, and if all goes smoothly, your /boot partition will remain as such. Note that the /boot partition is *not* the same as a BIOS Boot Partition, though; the latter is a specialized GPT-only partition for the benefit of GRUB 2. Read the link I provided earlier for details. You can create a BIOS Boot Partition in gdisk by creating a new partition and giving it a type code of EF02.

> When I change the type with fdisk, will this have effect on the data on it?

No. Changing the partition type code just changes one byte (on MBR disks) in the partition's description; the data stored in the partition itself remain untouched.

> I went through some articles (e.g. you links). Just to verify: 
I boot up the system with e.g. an Ubuntu Live. I convert the HDD with "gdisk /dev/sda". Then I reinstall grub with "grub-install /dev/sda". Is this all? Does this not destroy my lvm volume group?

You should create a BIOS Boot Partition as part of the conversion process, or immediately afterwards; but otherwise, yes, that's it. Your LVM will be unaffected. A couple of caveats, though:


[list]
[*]gdisk is not installed by default with Ubuntu, so you'll need to install it. With Ubuntu 10.04, you can do this by typing "sudo apt-get install gdisk"; however, this installs a rather elderly version (0.5.1, IIRC; the latest is 0.6.10). It's better to download the latest version from [its Sourceforge download page](https://sourceforge.net/projects/gptfdisk/files/) and install it by double-clicking its icon or by using the dpkg command.
[*]Any change to your partition table is potentially risky. Although I've done this conversion literally hundreds of times (mostly on non-bootable data disks), I can't guarantee that you won't run into problems. You should back up your data first. There are also occasional buggy BIOSes that [need coaxing to boot from GPT disks.](http://www.rodsbooks.com/gdisk/bios.html) FWIW, among my other tests, I've converted at least two disks with LVM configurations with no problems.
[/list]

---

### Post by darkdragon-001 on 2010-09-14
Well I am using Ubuntu server, so I don't have a GUI (but for boot disk I can boot from the desktop-version-cd).

I tried to convert to gpt:
I installed gdisk from sourceforge.
gdisk /dev/sda
-> "w" to convert
gdisk /dev/sda
-> n for new and created a 1024 KiB big bios boot partition with correct label (ef02) and so on between my boot partition and my data partition (used default values everywhere).
parted /dev/sda set 2 bios_grub on
grub-install /dev/sda
ERROR:
"/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly."

do I have to somehow update fstab file?
do I have to somehow mount the partition?
which module do I have to specify?

Moving partitions around just gave me some new ideas:
What of the following processes is the best one:
* create a new primary at the end. move contents with lvm from extended to the newly created primary. delete extended with logical. move the two primaries. create extended and logical at the end.

sda2(sda5) | sda4 | empty
sda2(sda5) | sda4 | sda3
empty	   | sda4 | sda3
sda4      | sda3 | empty
sda4      | sda3 | sda2(sda5)
'()' means logical inside extended

* create a new primary partition at the end. move the contents from the logical one to the new primary with lvm. then delete extended and logicial. create a new primary at their place. move stuff back. delete created primary at the beginning. and then create an extended and a logical partition at this place.

sda2(sda5) | sda4 | empty
sda2(sda5) | sda4 | sda3
empty | sda4 | sda3
sda2 | sda4 | sda3
sda2 | sda4 | empty
sda2 | sda4 | sda3(sda5)

* What about extending a partition used by lvm? Is it possible to do so and then allocate the newly created space without touching the data? If yes, I could take process one and don't need to delete primary and create extended at the end:
sda2(sda5) | sda4 | empty
sda2(sda5) | sda4->resized
empty	   | sda4->resized
sda4->resized | empty
sda4->resized | sda2(sda5)

Because I think moving the rest to the end, to create a logical partition inside will not solve the problem but keeping it for the next expandig...


For future projects what do you think is the best solution:
* just install OS with GPT
* just create new logical volumes and no new primary ones to add to lvm
* create new HDDs instead of extending an existing one (I am using VMware). Then add the new HDD to the lvm

---

### Post by srs5694 on 2010-09-14
> **darkdragon-001 said:**
> Well I am using Ubuntu server, so I don't have a GUI (but for boot disk I can boot from the desktop-version-cd).

I tried to convert to gpt:
I installed gdisk from sourceforge.
gdisk /dev/sda
-> "w" to convert
gdisk /dev/sda
-> n for new and created a 1024 KiB big bios boot partition with correct label (ef02) and so on between my boot partition and my data partition (used default values everywhere).
parted /dev/sda set 2 bios_grub on
grub-install /dev/sda
ERROR:
"/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

If I understand correctly, you did this from a CD/DVD boot, not from your regular system boot. In this case, a plain grub-install won't work because your regular /boot files aren't where they normally are. You may be able to work around the problem by mounting your regular /boot partition on /boot while the CD/DVD boot is running, and then using grub-install. There are other ways to do it, too, like using [Super GRUB Disk](http://www.supergrubdisk.org) to boot your normal system and then using grub-install from there.

> Moving partitions around just gave me some new ideas:
What of the following processes is the best one:
* create a new primary at the end. move contents with lvm from extended to the newly created primary. delete extended with logical. move the two primaries. create extended and logical at the end.

sda2(sda5) | sda4 | empty
sda2(sda5) | sda4 | sda3
empty       | sda4 | sda3
sda4      | sda3 | empty
sda4      | sda3 | sda2(sda5)
'()' means logical inside extended

If you've converted to GPT, the primary/extended/logical distinction no longer exists.

With a basically LVM-based system, it doesn't really make too much difference how many partitions you've got or which ones are primary or logical; the LVM system handles where logical volumes are placed. That said, in an LVM configuration it's probably best to have fewer partitions rather than more, simply to avoid fragmentation of the volume group, which can theoretically degrade performance. (I don't know offhand how smart the Linux LVM utilities are in laying out logical volumes. If they do few or no checks of such things, you could easily end up with heavily fragmented logical volumes if you use too many partitions, especially if you add them in strange orders.)

That said, in a virtual machine, you've got an added layer of indirection that makes it harder to judge what sort of performance impact you'll see from moving or resizing partitions. If the disk images use any sort of compression, it's probably best to minimize copying or moving within the disk images, since such operations are likely to increase the size of the disk images unnecessarily.

> * What about extending a partition used by lvm? Is it possible to do so and then allocate the newly created space without touching the data?

Yes, this is possible. There are basically two ways to do it:


[list]
[*]Use fdisk or gdisk to delete the existing partition and then create a new one *that starts at the original partition's start sector,* but that's bigger. Then use pvresize to resize the physical volume (partition's contents) to fill the new partition.
[*]Use a GUI LVM utility, such as system-config-lvm or kvpm, to perform both the partition and physical volume resizes at once.
[/list]


> For future projects what do you think is the best solution:
* just install OS with GPT
* just create new logical volumes and no new primary ones to add to lvm
* create new HDDs instead of extending an existing one (I am using VMware). Then add the new HDD to the lvm

GPT vs. MBR is an independent issue from how to manage LVMs. Personally, I prefer GPT on a Linux-only installation. It's got several minor advantages over MBR, such as CRCs and on-disk backups of its critical data structures to help detect and recover from errors, and its lack of the primary/extended/logical partition distinctions. It's also got one huge (but as yet only minimally important in the real world) advantage, in that it supports drives with more that 2^32 sectors (2 TiB, given the standard 512-byte sector size). Sooner or later we'll all be using GPT, so we all might as well start learning about it now.

As to extending a VMWare configuration, it's probably simpler to create new virtual disks as needed and then add them to an LVM configuration than to deal with expanding a virtual disk, modifying its partitions, and then adjusting the LVM setup to match, at least until you run out of virtual disks in the virtual machine. That said, it's been years since I used VMWare, so there could be some VMWare-specific quirks or features that might render my judgment invalid.

---

### Post by darkdragon-001 on 2010-09-14
> **srs5694 said:**
> If I understand correctly, you did this from a CD/DVD boot, not from your regular system boot. In this case, a plain grub-install won't work because your regular /boot files aren't where they normally are. You may be able to work around the problem by mounting your regular /boot partition on /boot while the CD/DVD boot is running, and then using grub-install. There are other ways to do it, too, like using [Super GRUB Disk](http://www.supergrubdisk.org) to boot your normal system and then using grub-install from there.
With mounting the /boot partition grub-install worked.


> **srs5694 said:**
> GPT vs. MBR is an independent issue from how to manage LVMs. Personally, I prefer GPT on a Linux-only installation. It's got several minor advantages over MBR, such as CRCs and on-disk backups of its critical data structures to help detect and recover from errors, and its lack of the primary/extended/logical partition distinctions. It's also got one huge (but as yet only minimally important in the real world) advantage, in that it supports drives with more that 2^32 sectors (2 TiB, given the standard 512-byte sector size). Sooner or later we'll all be using GPT, so we all might as well start learning about it now.

The fact that it supports over 2 TiB is indeed important to me. I was already considering this when I was buying the 

HDDs. But then, I decided to only use 2 TiB as a raid, because there would be problems with my BIOS on the physical 

hardware. On the virtual, it's no problem, like I tested at the moment :)

Thank you very much for your help.

---

