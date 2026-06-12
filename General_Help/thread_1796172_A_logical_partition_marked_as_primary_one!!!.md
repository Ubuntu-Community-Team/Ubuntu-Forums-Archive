---
title: "A logical partition marked as primary one!!!"
date: 2011-07-03
forum: General Help
---

### Post by hyfanious on 2011-07-03
Hi
Today due to losing one of my partitions (I call it here P1) by installing windows xp, I recovered it by "Parted"
P1 was a logical partition
but now 
P1 is marked as a Primary one
what can I do?

---

### Post by Rubi1200 on 2011-07-03
Hi,
this sounds like a job for Fixparts:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the page carefully and backup important data before proceeding.

If you are at all unsure about any of the output post it here first before doing anything.

---

### Post by srs5694 on 2011-07-03
If everything works correctly as it is, I recommend not doing anything. Any change to the partition table is at least potentially risky, so "if it ain't broke, don't fix it," as they say.

That said, without knowing more, I can't make that advice absolute. It could be that your partition table is in an inconsistent state that will cause problems in the future even if your OSes all boot. You might also be experiencing some specific problems that you haven't mentioned. Thus, if you need more advice, I recommend you post again with details of any problems you're having, along with the output of the following command:

```

sudo fdisk -lu

```

Post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags or it will become difficult to parse.

This information will give us what we need to make more specific recommendations.

Incidentally, I'm not trying to contradict Rubi1200; FixParts can do primary-to-logical and logical-to-primary conversions, within certain limits. It may be an appropriate tool to use, too, if you need to do such a conversion. I'm just reluctant to recommend you do anything specific with your partition table without knowing more about your situation. (I'm the author of FixParts, BTW.)

---

### Post by hyfanious on 2011-07-03
> **Rubi1200 said:**
> Hi,
this sounds like a job for Fixparts:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the page carefully and backup important data before proceeding.

If you are at all unsure about any of the output post it here first before doing anything.
Thanks for being so considerate
I got this result:
```


# partition table of /dev/sda
unit: sectors
  
/dev/sda1 : start=  3903795, size= 21302190, Id=83, bootable
/dev/sda2 : start= 25205985, size= 21302190, Id= 7
/dev/sda3 : start= 46508175, size= 17896410, Id= f
/dev/sda4 : start= 64404585, size=560732760, Id=83
/dev/sda5 : start= 46508301, size= 17896284, Id=83

```as u can see sda4 has inappropriate size
what should I do?

---

### Post by srs5694 on 2011-07-03
Why do you say that /dev/sda4 has an inappropriate size? It's 560,732,760 sectors, which is about 267 GiB. That's a perfectly reasonable size for a partition on many modern disks.

Please read my previous post and state any actual problems you're having (e.g., "Windows won't boot" or "GParted shows the disk as empty") as well as the fdisk (not sfdisk) output I requested.

---

### Post by hyfanious on 2011-07-04
> **srs5694 said:**
> Why do you say that /dev/sda4 has an inappropriate size? It's 560,732,760 sectors, which is about 267 GiB. That's a perfectly reasonable size for a partition on many modern disks.

Please read my previous post and state any actual problems you're having (e.g., "Windows won't boot" or "GParted shows the disk as empty") as well as the fdisk (not sfdisk) output I requested.
Hi again
this is the result of fdisk:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061982

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     3903795    25205984    10651095   83  Linux
/dev/sda2        25205985    46508174    10651095    7  HPFS/NTFS
/dev/sda3        46508175    64404584     8948205    f  W95 Ext'd (LBA)
/dev/sda4        64404585   625137344   280366380   83  Linux
/dev/sda5        46508301    64404584     8948142   83  Linux


```

I told it has an inappropriate size cause I was formated my hard disk by myself and this configurations is not mine
I sent a screen shot of gparted as an attachment
U can see that the sda4 is not more belongs to Extended area
just to know I say, according to ur previous post every thing works fine
all partitions are accessible and both OSes (ubuntu - Xp) have the same situation
But in fact if last partition (that u can see in gparted) will mark as a subpartition of Extended area every thing will be just as same as my initial configuration

I wanna let u know that my major problem is this:
swap area cannot activated any more(due to exceeding max. number of primary partitions)



thanks in advance

---

### Post by srs5694 on 2011-07-04
The simplest way to add swap space is to add a swap *file* rather than a swap *partition*. You can do it like this:


[list=1]
[*]Open a terminal window.
[*]Type "sudo dd if=/dev/zero of=/home/swap bs=1048576 count=2048". This creates a 2 GiB file in /home. Adjust the count value to change the size to whatever you like, and change the of= value if you want the swap file to reside somewhere else. (I picked /home because it seems to have the most free space.)
[*]Type "mkswap /home/swap"
[*]Add an entry to /etc/fstab, similar to the below.
[*]Type "swapon /home/swap" to activate swap space. Next time you reboot, be sure to check that it's active by typing "free -m". The last line shows swap space availability and use.
[/list]


```
/home/swap    none     swap    sw    0 0

```

If you really want a swap partition rather than a swap file, you'll need to juggle your partitions. The trouble is that logical partitions must be contiguous with one another and there must be at least one free sector before each logical partition. Given your current arrangement, the only way to expand your extended partition is to add /dev/sda2 or /dev/sda4 to it; but neither of them is preceded by a free sector, so you can't expand your extended partition without resizing at least one partition. You could decrease the size of /dev/sda5 to turn /dev/sda4 into a logical partition or you could decrease the size of /dev/sda2 to convert it to a logical partition; however, if you're booting Windows from /dev/sda2, that conversion would render it unbootable. Thus, to add a swap partition I recommend this:


[list=1]
[*]Using GParted, shrink /dev/sda5 by as small an amount as you can manage. Shrink it from its *end*, not from its beginning.
[*]Use FixParts to convert /dev/sda4 into a logical partition. It will become /dev/sda6.
[*]Reboot to ensure the computer is using the new partition table.
[*]Shrink /dev/sda6 (currently /dev/sda4) to make room for your new swap partition.
[*]Create your new swap partition inside the extended partition. It will probably be /dev/sda7.
[/list]

---

### Post by hyfanious on 2011-07-04
> **srs5694 said:**
> The simplest way to add swap space is to add a swap *file* rather than a swap *partition*. You can do it like this:


[LIST=1]
[*]Open a terminal window.
[*]Type "sudo dd if=/dev/zero of=/home/swap bs=1048576 count=2048". This creates a 2 GiB file in /home. Adjust the count value to change the size to whatever you like, and change the of= value if you want the swap file to reside somewhere else. (I picked /home because it seems to have the most free space.)
[*]Type "mkswap /home/swap"
[*]Add an entry to /etc/fstab, similar to the below.
[*]Type "swapon /home/swap" to activate swap space. Next time you reboot, be sure to check that it's active by typing "free -m". The last line shows swap space availability and use.
[/LIST]


```
/home/swap    none     swap    sw    0 0

```If you really want a swap partition rather than a swap file, you'll need to juggle your partitions. The trouble is that logical partitions must be contiguous with one another and there must be at least one free sector before each logical partition. Given your current arrangement, the only way to expand your extended partition is to add /dev/sda2 or /dev/sda4 to it; but neither of them is preceded by a free sector, so you can't expand your extended partition without resizing at least one partition. You could decrease the size of /dev/sda5 to turn /dev/sda4 into a logical partition or you could decrease the size of /dev/sda2 to convert it to a logical partition; however, if you're booting Windows from /dev/sda2, that conversion would render it unbootable. Thus, to add a swap partition I recommend this:


[LIST=1]
[*]Using GParted, shrink /dev/sda5 by as small an amount as you can manage. Shrink it from its *end*, not from its beginning.
[*]Use FixParts to convert /dev/sda4 into a logical partition. It will become /dev/sda6.
[*]Reboot to ensure the computer is using the new partition table.
[*]Shrink /dev/sda6 (currently /dev/sda4) to make room for your new swap partition.
[*]Create your new swap partition inside the extended partition. It will probably be /dev/sda7.
[/LIST]


in fact I had a swap area before
if u see again I have a 2 Gib free space on my table partition that used to be swap area but now it marked as a unallocated area
  I wanna re-enable it
see my previous attached file  -- before the sda1 I have a unallocated partition with 1.86 Gib Size

---

### Post by hyfanious on 2011-07-05
any help??

---

### Post by srs5694 on 2011-07-05
I've already answered your questions. Please re-read my last response.

---

### Post by dFlyer on 2011-07-05
> **hyfanious said:**
> in fact I had a swap area before
if u see again I have a 2 Gib free space on my table partition that used to be swap area but now it marked as a unallocated area
  I wanna re-enable it
see my previous attached file  -- before the sda1 I have a unallocated partition with 1.86 Gib Size

Try this:

sudo swapon /dev/sda1

if that is where it was before, that should turn swap back on.

---

### Post by srs5694 on 2011-07-05
> **dFlyer said:**
> Try this:

sudo swapon /dev/sda1

if that is where it was before, that should turn swap back on.

No, according to the GParted screen shot, /dev/sda1 contains an ext4 filesystem and is the Linux installation's root (/) filesystem. There *used to be* a partition *before* that one that was swap space. Hyfanious's problem is that it can't be re-created because there are no primary partitions left and that space is located such that it can't be used as a logical partition.

As I wrote in post #7, the solution is to shrink /dev/sda5 by a small amount, convert /dev/sda4 into a logical partition, and then create a new primary partition to get a new swap partition. Using a swap file would be easier and less risky, but hyfanious doesn't seem to want to do this.

---

### Post by hyfanious on 2011-07-06
> **srs5694 said:**
> No, according to the GParted screen shot, /dev/sda1 contains an ext4 filesystem and is the Linux installation's root (/) filesystem. There *used to be* a partition *before* that one that was swap space. Hyfanious's problem is that it can't be re-created because there are no primary partitions left and that space is located such that it can't be used as a logical partition.

As I wrote in post #7, the solution is to shrink /dev/sda5 by a small amount, convert /dev/sda4 into a logical partition, and then create a new primary partition to get a new swap partition. Using a swap file would be easier and less risky, but hyfanious doesn't seem to want to do this.

Well Thanks for understanding
I think if I can re-mark my last partition as a logical I will be able to re-enabled my swap area again
and if it's not possible I prefer to back up my files and re-format my partition
but I wanna know if there is any easier and safe solution without backing up about 180 Gib of data?

---

### Post by srs5694 on 2011-07-06
Your /dev/sda4 can only be turned into a logical partition if there's a gap between it and the preceding partition (/dev/sda5). Currently there's no such gap, so resizing /dev/sda5 is necessary. (You could instead resize /dev/sda4 by moving its start point, but that's much riskier and much more time-consuming.)

There's *always* risk when dealing with repartitioning operations. Personally, I would back up the contents of any partition before resizing it, unless I was prepared to lose it all. I would also back up the partition table itself before doing anything with it, as described on my [FixParts Web page.](http://www.rodsbooks.com/fixparts/) Some people are willing to live with the risks (or don't understand them) and so don't take these precautions. Others are even more cautious and so back up all data before doing any partitioning operation. (Of course, having a complete backup of your data is important in case of random disk failures, so you *should* have such a backup already, even if it's a few days or even weeks old.)

I've already presented one easier and safer way to do this: Use a swap file rather than a swap partition. It's unclear to me why you don't want to do this, but if you don't, you don't.

The only other option that qualifies as "easier" is to convert the disk to a GUID Partition Table (GPT) disk with a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) so that Windows can still boot. This would enable you to do the job without first resizing any partition; however, hybrid MBRs are flaky and dangerous, so I don't recommend you try this approach. You'll also have to re-install GRUB, and probably create a BIOS Boot Partition for it (there's room on your disk; this partition can be quite small), which can be difficult if you're not used to such operations. I mention this option only in the interests of being absolutely complete in my response; IMHO, it's not a good choice.

Other options might be better, but definitely not easier or quicker. These involve completely restructuring your disk through any number of combinations of backups, moves, and resizes of partitions. Some of these might end up necessitating a re-installation of Windows. You could get a more orderly layout this way, but it's probably not worth the hassle or the risk.

---

### Post by hyfanious on 2011-07-10
> **srs5694 said:**
> Your /dev/sda4 can only be turned into a logical partition if there's a gap between it and the preceding partition (/dev/sda5). Currently there's no such gap, so resizing /dev/sda5 is necessary. (You could instead resize /dev/sda4 by moving its start point, but that's much riskier and much more time-consuming.)

There's *always* risk when dealing with repartitioning operations. Personally, I would back up the contents of any partition before resizing it, unless I was prepared to lose it all. I would also back up the partition table itself before doing anything with it, as described on my [FixParts Web page.]("http://www.rodsbooks.com/fixparts/") Some people are willing to live with the risks (or don't understand them) and so don't take these precautions. Others are even more cautious and so back up all data before doing any partitioning operation. (Of course, having a complete backup of your data is important in case of random disk failures, so you *should* have such a backup already, even if it's a few days or even weeks old.)

I've already presented one easier and safer way to do this: Use a swap file rather than a swap partition. It's unclear to me why you don't want to do this, but if you don't, you don't.

The only other option that qualifies as "easier" is to convert the disk to a GUID Partition Table (GPT) disk with a [hybrid MBR]("http://www.rodsbooks.com/gdisk/hybrid.html") so that Windows can still boot. This would enable you to do the job without first resizing any partition; however, hybrid MBRs are flaky and dangerous, so I don't recommend you try this approach. You'll also have to re-install GRUB, and probably create a BIOS Boot Partition for it (there's room on your disk; this partition can be quite small), which can be difficult if you're not used to such operations. I mention this option only in the interests of being absolutely complete in my response; IMHO, it's not a good choice.

Other options might be better, but definitely not easier or quicker. These involve completely restructuring your disk through any number of combinations of backups, moves, and resizes of partitions. Some of these might end up necessitating a re-installation of Windows. You could get a more orderly layout this way, but it's probably not worth the hassle or the risk.

thanks very much
after all I did repartitioning
;)
Now every thing seems correctly
just one another and somehow different question
I have this partitions:
1. swap
2. primary Ubuntu
3. primary Fedora(don't be mad at me , just for testing ;) )
4. extended(contains two logical partition)

if there is any way that I can allocate another primary partition for windows, let me know,
tnx in advance

---

### Post by srs5694 on 2011-07-10
> **hyfanious said:**
> I have this partitions:
1. swap
2. primary Ubuntu
3. primary Fedora(don't be mad at me , just for testing ;) )
4. extended(contains two logical partition)


You can only do that by converting one of your primary partitions into a logical partition (or deleting it altogether). Given the current layout, this would have to be the Fedora partition, although you could move partitions around or delete the swap partition and re-create it as a logical partition. FixParts can do a primary-to-logical conversion, but only if there's a gap of at least one sector between the partition you're converting and the one before it.

---

### Post by hyfanious on 2011-07-10
> **srs5694 said:**
> You can only do that by converting one of your primary partitions into a logical partition (or deleting it altogether). Given the current layout, this would have to be the Fedora partition, although you could move partitions around or delete the swap partition and re-create it as a logical partition. FixParts can do a primary-to-logical conversion, but only if there's a gap of at least one sector between the partition you're converting and the one before it.

Thanks in Advance for all these usefull tips
:)

---

