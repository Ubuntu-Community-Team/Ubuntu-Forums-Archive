---
title: "Install Windows as Dual Boot After Ubuntu (on LVM Partitions)"
date: 2011-02-07
forum: General Help
---

### Post by Chrison999 on 2011-02-07
Hi, all!

I'm running Ubuntu 10.10 on a 600GB hard drive that is partitioned as follows, according to GParted:

/dev/sda1 = ext4 = /boot = 100MB
/dev/sda2 = extended = 600GB
/dev/sda6 = ext4 = / = 140GB
/dev/sda7 = ext4 = /home = 450GB
/dev/sda5 = swap = 6GB

Partitions sda2 through sda7 are all LVM volumes.  While I have free space within the volumes, the volumes take up all of the hard drive (i.e. there is no unpartitioned space on the hard drive).

I now have an application I must run under Windows.  I have tried WINE, VirtualBox and VMWare, but none of these methods have worked for a variety of reasons.  So, I now want to resize my partitions to free up some space (not much, maybe 30-40GB) so I can install Windows on a dual boot setup.  By the way, I have backed up my important data (I may be bold but I'm not stupid!)  :p

So, I *think* this is what I do now:

1.  Resize one of the LVM volumes to free up some space on the volume.  (I'm thinking I will use the "/home" partition for this.)

2.  Use GParted to reduce the size of that partition (/dev/sda7 if I use "/home") on the physical hard drive, thus freeing up space on the drive.

3.  Create a new NTFS partition using the freed-up space.

4.  Install Windows on the new NTFS partition.

5.  Modify grub so that it presents a screen allowing me to pick the O/S I want to boot.

Is this the correct procedure for doing this?  Are there any "gotchas!" I need to be aware of?  Are there any FAQs or HOW-TOs to walk me through this?

Thanks, in advance, for any advice/tips provided.

Regards,

Chris

P.S.  Attached is a screenshot of the GParted screen in case that's helpful.

---

### Post by srs5694 on 2011-02-07
First, you do *not* have a Logical Volume Manager (LVM) configuration. Partitions 5 and up are logical *partitions*, not logical *volumes*. Partition 2 is an *extended partition*. None of these partition types has anything to do with LVM. For purposes of this specific post, this is largely a terminology issue, since you haven't mentioned anything that's *really* LVM-specific, aside from the acronym. I just want to get this straightened out so that you don't start reading up on LVMs and get really confused!

Second, I note that your root (/) partition (/dev/sda5) is 140 GB in size, and you've got a separate /home partition (/dev/sda6, 450 GB). Ordinarily, 5-20 GB is plenty big for a Linux root (/) partition for a desktop system when there's a separate /home partition. I see, however, that you've got just under 38 GB in use on your root (/) partition. There can be legitimate reasons for that, but it could be you've got a lot of unnecessary files cluttering the partition. Try typing "sudo apt-get clean" in a terminal and see if that clears up some space. Fixing this (or determining what legitimate cause there is) isn't vital before you proceed, but I'd recommend taking care of it, since you may need to move that partition before you install Windows, and you don't want to have to move data unnecessarily. Doing so would take time and increase the risk of problems that could trash your whole installation.

A related issue is that you should be able to take most or all of the space you need from the root (/) partition rather than from the /home partition, particularly if you can delete enough unnecessary files from the root (/) partition to get its consumed-space value down to the 10 GB or less that is common. If you can get away with moving/resizing just one Linux partition rather than two, that's good.

Alternatively, you could shrink the /home partition by changing its end point and put the Windows partition *after* the Linux partitions. (You'll have to move or delete and then re-create your swap partition, but that's not as dangerous as mucking with filesystem partitions.) This sort of placement of a Windows partition is unorthodox, but it should work. This would have the advantage of not needing to move the start of any Linux partition. Moving the start of a partition is much more time-consuming and dangerous than moving the partition's end point.

No matter what you do, you'll have to move and/or resize your logical partitions and then adjust the size of the extended partition to match. The reason is that Windows *must* install in a primary partition; it won't install in a logical partition. (I've seen some indications that it will sometimes try to do so, but will then trash your partition table, so don't even try to install Windows to a logical partition.) Primary partitions cannot exist inside an extended partition, so you must move/resize the logical partitions to consolidate free space at the start or end of the extended partition and then resize the extended partition so that the free space is outside the extended partition and therefore available for use by a new primary partition. Fortunately, you've only got two primary partitions now (counting the extended partition as a primary), so you can create up to two more primary partitions, once you've adjusted your partitions' sizes.

I recommend creating two new partitions: A primary partition for the Windows boot partition and a primary or logical partition (preferably a logical partition) for an inter-OS data exchange partition. It's safer to use a non-boot partition for exchanging data between the OSes than it is to give one OS access to another's boot partition. You'll have to judge how to size each of these partitions yourself. When you create them in GParted, make the Windows boot partition NTFS and make the data-exchange partition either FAT or NTFS. FAT is likely to be less troublesome if you won't need to exchange files larger than 4 GiB, but NTFS is necessary if you need to exchange larger files.

You'll have to make all your partition changes using a live CD; GParted won't work on a partition that's currently mounted (that's what those key icons mean in the GParted screen shot you've posted).

After you install Windows, Windows will boot but Linux won't. You'll have to re-install GRUB to get it booting again. You can use [Super GRUB 2 Disk](http://www.supergrubdisk.org/) to boot Ubuntu and then type "sudo grub-install /dev/sda" in a Terminal to re-install GRUB. I think that should also detect Windows and let you select it from GRUB's menu, but if not, "sudo update-grub" will do the job.

Before you do anything, make backups. Back up your partition table by typing "sudo sfdisk -d > parts.txt" at a shell prompt. (Do this before and after making your changes in GParted, changing the filename "parts.txt" for the second backup.) Copy the files to a USB flash drive or some other removable medium. If Windows messes up too badly, you may be able to recover easily by restoring the partition table alone. You should also back up your Linux installation, or at least any important data, before you attempt to resize anything. Partition resizing operations are inherently risky, and if things go badly, having a backup will ease recovery.

Aside from these corrections and pointers, you've got the right basic idea for how to proceed.

---

### Post by Chrison999 on 2011-02-07
> **srs5694 said:**
> 
First, you do *not* have a Logical Volume Manager (LVM) configuration.... I just want to get this straightened out so that you don't start reading up on LVMs and get really confused!


Thank you VERY much for that helpful response!  I posted that message for two reasons:  (1) I *thought* I might be going the right direction but wasn't sure, and (2) I *have* been reading up on LVMs and was getting *really* confused because what I was reading wasn't matching with what I was seeing on my system!  So, you have likely saved me from doing something inadvertent to really screw things up.

> **srs5694 said:**
> 
Second, I note that your root (/) partition (/dev/sda5) is 140 GB in size, and you've got a separate /home partition (/dev/sda6, 450 GB). Ordinarily, 5-20 GB is plenty big for a Linux root (/) partition for a desktop system when there's a separate /home partition.


Now that you mentioned it, I see that too.  I have done some wandering around and have discovered quite a few data directories I thought were sitting over in /home that are over on root (for instance, in /usr/share).  I'm now in the process of moving that stuff over to /home where it should be.  Once that's done, I'll run "sudo apt-get clean" and see if that also clears-up some space.

> **srs5694 said:**
> 
 A related issue is that you should be able to take most or all of the space you need from the root (/) partition rather than from the /home partition...


That would be my preference, as I don't really need that much space for Windows and, as you said, that would be the easier way to go.

So, for now I'm busy doing a general clean-up of the system.  Once that's done, I'll do another backup and then take a harder look at the rest of your reply.  If I have any questions, I'll come back here and ask before proceeding.  As I said in my original post, I'm not stupid!  Whenever I do something this complex and possibly-risky, I *always* try and make sure I know exactly what I'm doing before I'm doing it.  Even then there's a risk of things going terribly wrong, but the risk is much less than if I were to just bumble into things without knowing/understanding what I'm doing.

Thanks, again, for your help!  I'll keep you (and everyone else) posted as to my progress.

Regards,

Chris

---

### Post by srs5694 on 2011-02-07
> **Chrison999 said:**
> I have done some wandering around and have discovered quite a few data directories I thought were sitting over in /home that are over on root (for instance, in /usr/share).  I'm now in the process of moving that stuff over to /home where it should be.  Once that's done, I'll run "sudo apt-get clean" and see if that also clears-up some space.

Be careful with that. Ordinary users (that is, you except when you use sudo) shouldn't be able to write to most directories in /usr, including /usr/share and its subdirectories. It's possible that you're seeing something that just happens to have the same name as one or your files or directories or that really is a system file. You can check if a file was installed as part of a package using the -S option to dpkg:

```

$ **dpkg -S /usr/share/X11/rgb.txt**
x11-common: /usr/share/X11/rgb.txt

```

This example shows that /usr/share/X11/rgb.txt is part of the x11-common package. If a file you're thinking of moving is part of a package, don't move it. A few files are system files but aren't part of a package. The Microsoft TrueType fonts are like that, for example.

If you're really seeing your personal data files stored in /usr, then chances are you've been overusing sudo and making mistakes with it. If that's the case, you should rethink how and why you're using sudo. (I see too many posts on this site recommending that people use sudo to overcome permissions issues that are better handled in other ways, such as changing mount options on NTFS partitions or coordinating UID values across multiple installations.) Most desktop Ubuntu users should not need to use sudo all that often, but it's easy to overuse it because it's an easy way to overcome certain problems. It can be a bit like using a sledgehammer to get from one side of a fence to another when there's a gate a few feet away, though.

---

