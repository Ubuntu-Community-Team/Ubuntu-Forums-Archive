---
title: "Add new logical partition"
date: 2010-09-23
forum: General Help
---

### Post by Th3P4rk2 on 2010-09-23
Hiya all,Cheers for the help before just got another little problem I cant seem to work around.

I am triple booting my laptop, heres what my hard drive partitioning looks like at the minute;



Primary 1) /dev/sda1 =  Dedicated Boot (grub2)

(125567mb free space)

Extended logical 1) /dev/sda5 = Ubuntu (already installed)
Extended logical 2) /dev/sda6 = backtrack (trying 2 install)

Primary 2) /dev/sda2 = NTFS (Win 7 already installed)

(77046mb Unusable)

Primary 3) = Swap

Right, first things first.

I have my other laptop on at the minute and am at the prepare partition screen on backtrack 4, its identical to the ubuntu installer partition screen, I want to install backtrack into Extended logical 2 /dev/sda6 as above...what do I put as the mount point? This will be the least used OS.

Next question, I am wanting to use the (free space) above as a shared area between windows and linux but odviously already have my 4 partitions used up...I am now wanting to delete my swap partition and create a new logical partition for swap within the extended partition above. Can I do this without having to format and start all over again? if so how is it done?

And finally what is the unusable space above? brand new expensive HP laptop so not damaged blocks I hope, any ideas how I can find out why this is unusable or allocate it to one of the other partitions? I would have though it would have automatically become part of the (free space) when it was made available.

Your support is much appreciated anyway, Thanks in advance!

Antony

---

### Post by spiky001 on 2010-09-23
Hi see if I can help, why not load bt4 on sad6 allow a swap of what you need, then use that same swap for ubuntu,then get rid of other swap, The unusable space I take it needs formating so both systems can use it hope this helps, If I have made some mistakes some1 correct me

---

### Post by srs5694 on 2010-09-23
> **Th3P4rk2 said:**
> Hiya all,Cheers for the help before just got another little problem I cant seem to work around.

I am triple booting my laptop, heres what my hard drive partitioning looks like at the minute;

Primary 1) /dev/sda1 =  Dedicated Boot (grub2)

(125567mb free space)

Extended logical 1) /dev/sda5 = Ubuntu (already installed)
Extended logical 2) /dev/sda6 = backtrack (trying 2 install)

Primary 2) /dev/sda2 = NTFS (Win 7 already installed)

(77046mb Unusable)

Primary 3) = Swap

Right, first things first.

I have my other laptop on at the minute and am at the prepare partition screen on backtrack 4, its identical to the ubuntu installer partition screen, I want to install backtrack into Extended logical 2 /dev/sda6 as above...what do I put as the mount point? This will be the least used OS.

The main mount point for *any* Linux installation is root (aka "/"). If you split the installation across multiple partitions, you'll use other mount points for the additional partitions -- /home, /usr, /opt, /boot, or whatever.

> Next question, I am wanting to use the (free space) above as a shared area between windows and linux but odviously already have my 4 partitions used up...I am now wanting to delete my swap partition and create a new logical partition for swap within the extended partition above. Can I do this without having to format and start all over again? if so how is it done?

Yes, it can be done. You may need to expand the extended partition backwards -- it's unclear if this is necessary since you only summarized your partition table. With this done, you'll have to either delete and re-create the swap partition or copy it. GParted provides options to do both things, although I'm not sure if copying would work in this case. You may need to do some of these things from an Ubuntu Live CD or some other Linux emergency disc, since you can't operate on any partition that's currently active. If you delete and re-create swap, you'll need to edit /etc/fstab to change the UUID of the swap partition, or refer to it by device filename rather than by UUID.

If you need more specific advice, please post a screen shot of GParted or the output of "fdisk -lu", preferably between a [noparse]```
[/noparse] and [noparse]
```[/noparse] string for legibility.

> And finally what is the unusable space above?

You've already said why it's unusable: You've already used your four primary partitions. The "unusable" space is between two primary partitions, so you can't add it to the existing extended partition and you can't create a new primary partition where it is.

Offhand, I can think of four ways to render that space usable:


[list]
[*]Move the Windows partition up in the disk, thus moving the free space to between the extended partition and the Windows partition. This will enable you to expand the extended partition and create logical partitions or resize the existing logical partitions into the free space. Note, however, that moving the Windows partition with Linux tools will almost certainly render Windows unbootable. The Windows partitioning tool might do the job, but I'm not positive of that. Alternatively, but in a similar way, you could delete the partition, create a new one at the end of the disk, and re-install Windows to it.
[*]You can delete one primary partition, thus enabling you to create a new primary partition. Since you say you want to move swap space, which is currently on a primary partition, onto a logical partition, this may be a good option. You'll need to create a single primary partition that covers the new free space area; you won't be able to create more than one partition unless you delete another primary partition. This option also will not enable you to resize your existing Linux partitions into this area of the disk, although you could mount that space in Linux.
[*]You can convert the disk from Master Boot Record (MBR) form to GUID Partition Table (GPT) form. GPT doesn't have the primary/extended/logical partition distinction or the headaches that come with it. The big drawback is that Windows can't boot from GPT on a BIOS-based computer. There is a workaround, known as a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) in which up to three partitions may be defined for the benefit of GPT-unfriendly OSes. You'd put the Windows partition, and perhaps another data-exchange partition, in the hybrid MBR, and Linux would use all its partitions as GPT partitions. IMHO, hybrid MBRs are ugly and dangerous, so I don't generally advise their use; but your other options are equally ugly and dangerous, or at least inflexible, so this approach might be worth investigating. To convert to GPT, you'll need to use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program, and after the conversion you'll need to re-install GRUB 2.
[*]Wipe out everything on the disk and start again. This is tedious, but at least you could set the disk up optimally without dealing with partition resizing or moving operations. This may not be an appealing option if you've got much data you want to keep on the disk already, though.
[/list]


I'm not sure which of these options is best. To some extent it depends on your own needs and skill level, how much data you've got installed, and other details that I can't know.

---

