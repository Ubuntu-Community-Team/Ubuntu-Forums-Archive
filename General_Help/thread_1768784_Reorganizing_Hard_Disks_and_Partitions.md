---
title: "Reorganizing Hard Disks and Partitions"
date: 2011-05-27
forum: General Help
---

### Post by fantab on 2011-05-27
I am relatively new to Linux and have been Dual Booting Ubuntu 'Lucid Lynx'x64 with Windows 7 x32.

I have recently bought a new 1TB HDD and have been using it as /dev/sdb with Lucid. Windows is on /dev/sda. I have changed my BIOS to boot sdb first. 

I have decided that I want to use Ubuntu Lucid my main OS and hence I want to make my sdb sda, and sda sdb.

Q: **Will there be any problems when booting?** I ask this because GRUB is presently installed on /dev/sdb which will become /dev/sda.

My present partition scheme for /dev/sdb is:

```
/dev/sdb1   ext4      /       30gb    boot
/dev/sdb4   extended         150gb
/dev/sdb6   ext4      /Home  146gb
/dev/sdb5   swap               4gb
/dev/sdb2   ext4             250gb
/dev/sdb3   ext4             500gb 
```

As you can see the partitions numbers are 'messy'. I want to re-partition my HDD as following:

```
/dev/sdb1   ext4             500gb    
/dev/sdb2   ext4             200gb
/dev/sdb3   ext4      /Lucid  32gb
/dev/sdb4   extended         200gb
/dev/sdb5   ext4      /Home  145gb
/dev/sdb6   ext4              50gb 
/dev/sdb7   swap               4gb
```

I think this scheme is very simple and looks neat. 

Q. **Will there be any problems if I use /dev/sdb3 for / mountpoint?** I ask this because I have personally never used any other partition other than the first to install any OS.

I understand that if I am going to re-partition and reformat my HDD my earlier question is irrelevant, yet I would like to know the answer.

Please clear my doubts.

Thanks.

---

### Post by oldfred on 2011-05-27
I would not change sda & sdb. Ubuntu would be ok with the change as it uses UUIDs, but windows can have issues and works best from sda.

I left my XP in my sda and have Ubuntu in sdb & sdc (several installs). Partitions do not have to be organized in any order. When I get a new drive every few years I do try to reorganize, but over time it gets messed up.

Not really an optimal organization as now it is a couple of years of changes:

```
Device           UUID                                   TYPE       LABEL

/dev/sda1        04B05B70B05B6768                       ntfs       WinXP
/dev/sda2        13a684e4-2849-4566-9528-21cd07028a9a   ext3       backup
/dev/sda4        46CD-C9B2                              vfat       SHARE
/dev/sdb2        0eea4e95-ea0a-4745-80d4-57bf2bbc9d69   ext4       Maverick
/dev/sdb3                                               swap       
/dev/sdb4        431ba9e5-c72c-41c2-ba82-d8ee052336ff   ext4       MavData
/dev/sdc1        9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f   ext3       grub
/dev/sdc10       b8a7e331-a716-4ac1-bf58-6ac515606c6d   ext4       newhome
/dev/sdc11       09367687-86d1-4fd0-9b81-2787d3196159   swap       
/dev/sdc12       07e2a08d-37ca-4cf1-877b-f02b0eabcbca   ext4       Puppy
/dev/sdc13       318fd41e-4210-4960-a0d9-ee9b48388d69   ext4       natty
/dev/sdc14       5c703dd6-c2aa-4b09-a690-7d1cb88283a9   ext4       
/dev/sdc15       2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9   swap       
/dev/sdc2        44332FD360AA9657                       ntfs       Shared
/dev/sdc5        117412d5-2dbe-4011-8aec-ae310d1ee6c7   ext4       Karmic
/dev/sdc6        a55e6335-616f-4b10-9923-e963559f2b05   ext3       Data
/dev/sdc7        5e25282c-9c54-45df-9e79-514011e98648   ext4       LUCID
/dev/sdc8        af29c61a-34e9-48eb-9c94-afcb4bb61582   ext4       Test
/dev/sdc9        F6A6-705D                              vfat       OLDG

```

---

### Post by Rebelli0us on 2011-05-27
I wouldn't do it.  BIOS or Grub will boot any disk you want (as you have been doing).

---

### Post by srs5694 on 2011-05-27
First, disk identity as /dev/sda vs. /dev/sdb is mostly irrelevant to Linux, with a few caveats. A disk won't normally be any faster, more reliable, or in any other way better if you swap cables around so that it's /dev/sda rather than /dev/sdb. You might have to change some configuration files, though (but, as oldfred says, *probably* not with recent versions of Ubuntu, since Ubuntu uses UUIDs to identify disks). Also, if your motherboard uses two different types of disk controller, you might see a change in performance by swapping cables, but that won't be because of a change in identity per se; it'll be because the disk hardware has changed. If you think that's the case for your computer, please elaborate. As a general rule, it's best to assume no difference in performance between disk connectors.

Second, it's not clear to me that your preferred configuration is any better than what you've got now. The partition order might be a little bit less confusing, but swap space is generally best placed in the middle of a set of Linux partitions, in order to minimize head movements when accessing it. (OTOH, if you've got enough RAM, you're not likely to use swap much, so this consideration isn't as important as it once was.) If you want to optimize your disk performance, it's critical to know what each partition does. You've got quite a few, and the purpose of most of them is unclear, so it's impossible to evaluate it. You might do better to consolidate partitions, which simplifies configuration and reduces the odds of your running out of space on one, than to juggle their locations, which is likely to be time-consuming and at least a bit risky.

If you want to reorganize just to get partitions in on-disk order, it may be possible to do that without moving the filesystems they contain. In theory, there are at least two ways to do this:


[list]
[*]Use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert the disk from the Master Boot Record (MBR) partitioning system it now uses to the GUID Partition Table (GPT) system. This eliminates the primary/extended/logical partition distinctions, which will enable you to get the sector order of the partitions to match the partition number order, thus reducing potential confusion over that issue. The downside is that you'll need to re-install your boot loader, and you'll probably need to create a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) to hold some GRUB code. (It can be as small as 32KiB, so you should be able to squeeze it in somewhere.) Also, Windows can't boot from a GPT disk on a BIOS-based computer, so if you think you might want to install Windows on this disk in the future, it might not be a good option.
[*]You can use [FixParts](http://www.rodsbooks.com/fixparts) to juggle the primary/logical status of your partitions. In principle, you could convert partitions at the end of the disk to logical, while keeping or converting the first 1-3 partitions as primaries. That'll get the order to match. The problem, in practice, is that there are restrictions on what can be primary vs. logical, so you might need to shrink some partitions by a tiny amount to enable some of these conversions. (The FixParts Web page describes the rules.) You'll need to run the program to see what could be done. Also, FixParts makes no guarantees about the order of the primary partitions it produces, so if in-order partitions are your goal, you might need to adjust them in fdisk afterwards. (FixParts does order logical partitions sequentially when it saves the partition table.)
[/list]


IMHO, it's not worth trying to adjust the order of partitions just to keep the sector orders and ID orders in sync. They're likely to get disordered again if/when you adjust your partitions, and there's always a risk of something going wrong -- a partitioning tool could fail and completely trash your partition table, or an OS might rely on partition order or some other feature that changes and become unbootable. I'm just presenting these options in case you really do have some compelling reason to make changes but something short of a complete wipe and restore could help you get it done more quickly.

Be sure to back up your data before making any major changes!

---

### Post by fantab on 2011-05-27
Thank you all for the replies and great suggestions. Your posts have been very informative.

[QUOTE=oldfred]Ubuntu would be ok with the change as it uses UUIDs, but windows can have issues and works best from sda.[/QUOTE]

For one I definitely won't be changing my HDD order, I will keep sda as sda... since Windows "works best from sda".

[QUOTE=srs5694]The partition order might be a little bit less confusing, but swap space is generally best placed in the middle of a set of Linux partitions, in order to minimize head movements when accessing it. (OTOH, if you've got enough RAM, you're not likely to use swap much, so this consideration isn't as important as it once was.) 

If you want to optimize your disk performance, it's critical to know what each partition does. You've got quite a few, and the purpose of most of them is unclear, so it's impossible to evaluate it. You might do better to consolidate partitions, which simplifies configuration and reduces the odds of your running out of space on one, than to juggle their locations, which is likely to be time-consuming and at least a bit risky.[/QUOTE]

OK... I have a couple of more questions:

Firstly, I have 2gb DDR2 800mhz memory RAM. **Where should I place the SWAP? If it has to be in the middle then can I make and use /dev/sdb5 logical as swap?**

```
/dev/sdb1   ext4             500gb    
/dev/sdb2   ext4             200gb
/dev/sdb3   ext4      /Lucid  32gb
/dev/sdb4   extended         200gb
/dev/sdb5   ext4      /Home  145gb
/dev/sdb6   ext4              50gb 
/dev/sdb7   swap               4gb

```

Secondly, the 500gb sdb1 [presenly, sdb2] and 200gb sdb2 [presently, sdb3] are to store my personal data like, videos, music, ebooks, documents... etc.

I will be creating extra  50gb /dev/sdb6 for any other linux distro I might want to try. For instance I wanted to try Fedora and due to lack of foresight during partitioning, I was forced to use 200gb partition. What a waste of HDD real estate.

And since I am willing to delete all existing partitions (I'm not going to juggle anything as it is) and create new and re-install Lucid lynx, I am not really inclined to vex myself with GDisk or FixParts now. They were, however, very good suggestions for any future need. 

**So should I proceed with my scheme of Hdd partitioning?**

Thank you all.

---

### Post by srs5694 on 2011-05-28
> **fantab said:**
> Firstly, I have 2gb DDR2 800mhz memory RAM. **Where should I place the SWAP? If it has to be in the middle then can I make and use /dev/sdb5 logical as swap?**

Swap *can be* just about anywhere. The physical location in the center of a cluster of Linux partitions optimizes performance when swap is used, but if you have enough memory, swap isn't likely to be used much. 2 GB is enough for now for most desktop uses, but you might hit swap a bit if you run lots of programs or very memory-hungry programs or if you run a program with a big memory leak.

It doesn't matter whether swap space is on a primary partition, a logical partition, or some other type of storage (like in an LVM's logical volume -- see below).

quote]Secondly, the 500gb sdb1 [presenly, sdb2] and 200gb sdb2 [presently, sdb3] are to store my personal data like, videos, music, ebooks, documents... etc.[/quote]

Why have two partitions for this, plus a /home partition? That's a lot of unnecessary complication, IMHO. Just use one big /home partition for all your personal files. You can even share it across distributions -- you just have to be careful to use different home directories for each distribution (as in /home/fantabu for Ubuntu and /home/fantabf for Fedora) so that the user configuration files don't stomp on each other.

> I will be creating extra  50gb /dev/sdb6 for any other linux distro I might want to try. For instance I wanted to try Fedora and due to lack of foresight during partitioning, I was forced to use 200gb partition. What a waste of HDD real estate.

If you expect to be trying multiple distributions or need to change your partition layout frequently, I strongly recommend you look at Linux's [Logical Volume Manager (LVM).](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/) This is a way to take one or more partitions and split the space up again in different ways. It's most useful if you've got two or more small disks and want to create a filesystem that's too big for any one disk, but it's also useful if you regularly change your partitions. This is because a logical volume (which is a carrier for a filesystem, much like a partition) need not be physically moved to make room for another logical volume. The LVM subsystem allocates logical volumes much like a filesystem allocates files, so you don't need to worry about details like which sectors are assigned to which partitions and whether there's enough contiguous disk space for your purposes. In your situation, you could allocate most of your space, leaving some unallocated, and then add a new logical volume for Fedora later; or you could allocate all your space and, if you want to install another distribution later, you can shrink one or more existing volumes to make the space you need. You can do this with partitions too, of course, but you might need to *move* partitions, which is time-consuming and risky. You don't need to move logical volumes, since LVM can create new logical volumes in available space that's not contiguous. (Doing so degrades performance, but chances are you'd lose more time in total doing all the moving, and the moving operations are risky.)

If you use LVM, it's best to create two or three ~200 MiB partitions to be used as /boot partitions by any OSes you might want to install. (GRUB 2 can read LVM data structures, but GRUB Legacy can't, so if you want to install an OS that uses GRUB Legacy, it might insist on having /boot outside of the LVM.) You'd then create an LVM partition, carve it up into logical volumes, and install your OS(s).

Fedora uses LVM if you feed it a blank disk and tell it to install using its default options. Unfortunately, you've got to jump through some extra hoops to get Ubuntu to install to an LVM -- you've got to manually load the LVM software in the installer, then install it manually to the just-installed system *before* you reboot, since the installer is too stupid to realize it just installed to an LVM without the necessary software.

LVM is basically a Linux-only technology, so if you dual-boot with Windows, you'd need to leave Windows, as well as any shared-data partition you might have, out of the LVM configuration. For a system that's mostly or exclusively a Linux box, though, LVM is a big plus, albeit one that has a learning curve associated with it.

---

### Post by fantab on 2011-05-28
Thank you **srs5694** for yet another informative post.

[QUOTE=srs5694]Why have two partitions for this, plus a /home partition? That's a lot of unnecessary complication[/QUOTE]

:) I have been a windows user for quite a time now. Where I never ever store my data in the :c drive... because we never know when windows would crash. So I always move my data to other partitions. Similarly, I am wary of /Home to store all my Data... the Paranoia stems from the fact of losing precious data before. I understand that I am in Linux's, supposed, safe hands... yet like they say "better safe than sorry". 

Moreover, I will be using Windows for sometime to come. Professionally I need it because of my familiarity with certain windows specific software, which is also used at the workplace... So Windows will stay on my Home Desktop. But for every thing else I have moved successfully to Linux. Hence... the LVM option is not feasible because of its unfriendliness to Windows. 

I always wondered what LVM was and Thanks to your information and the provided link I know a lot about LVM. 

And since, "the physical location in the center of a cluster of Linux partitions optimizes performance when **swap** is used", I will stick to my scheme of Partitions.

I thank you a lot for all the information and help.

(As all my doubts are clarified I am marking this thread as SOLVED).

---

