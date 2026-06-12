---
title: "Out of space on Win (powered by Fedora, Ubuntu &amp; WinXP)"
date: 2009-11-23
forum: General Help
---

### Post by astrobob.tk on 2009-11-23
Hello guys,

I have a Dell 8600 laptop running on Ubuntu 9.04 (main OS), Fedora 11 (not being used), & WinXP (used on occasions).

My Win partitions are out of disk space & having the Fedora 11 with space not being used, I was wandering if it is possible to reduce the disk space used by Fedora to make more space for the Win partitions without corrupting or taking the risk of destroying any data.

I seek your help as I am a newbie in Ubuntu (just a few months) & Linux in general (only 2 yrs).

P.S.: the fedora OS is not listed in the menu list & I forgot the command after I press 'c' in the menu list.

I hope you could help in that 

Thank you in advance
BOB

---

### Post by prshah on 2009-11-23
> **astrobob.tk said:**
> 
My Win partitions are out of disk space & I was wandering if it is possible to reduce the disk space used by Fedora to make more space for the Win partitions without corrupting or taking the risk of destroying any data.

The risk is always there. Please do a backup before attempting this procedure.

Yes you can do this. The complexity will depend on your partition layout. Can you boot into Ubuntu, open a terminal (Applications-Accessories-Terminal) and post back the output from the following command```
sudo fdisk -l
``` This will tell us how your partitions are currently laid out.

You can then use Gparted (System-Administration-Partition Editor) to resize your Fedora and Windows partitions. More specific details can be given once the above requested output is studied.

Please post back with the requested information for more relevant and accurate steps.

---

### Post by astrobob.tk on 2009-12-16
well here is the result:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23a323a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1657    13309821    7  HPFS/NTFS
/dev/sda2            1658        6756    40957717+   f  W95 Ext'd (LBA)
/dev/sda3            6757        9434    21504000   83  Linux
/dev/sda4            9434        9729     2376622+  82  Linux swap / Solaris
/dev/sda5            1658        3314    13309821    7  HPFS/NTFS
/dev/sda6            3315        6475    25390701   83  Linux
/dev/sda7            6476        6756     2257101   82  Linux swap / Solaris

```

---

### Post by prshah on 2009-12-17
> **astrobob.tk said:**
> ```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1657    13309821    7  HPFS/NTFS
/dev/sda2            1658        6756    40957717+   f  W95 Ext'd (LBA)
/dev/sda3            6757        9434    21504000   83  Linux
/dev/sda4            9434        9729     2376622+  82  Linux swap / Solaris
/dev/sda5            1658        3314    13309821    7  HPFS/NTFS
/dev/sda6            3315        6475    25390701   83  Linux
/dev/sda7            6476        6756     2257101   82  Linux swap / Solaris

```

OK this is a sweet little nightmare of a setup. You have probably skipped one line of the fdisk output, something about "Partition table entries are not in disk order".

Assumptions (Please correct if wrong, instructions will change):
[indent] -> /dev/sda3 & 4 are related to your Ubuntu installation and /dev/sda6 & 7 (within the secondary partition) are related to your Fedora installation.

-> You want to increase space in /dev/sda1 Windows partition, not /dev/sda5 (within the secondary partition)

-> You have available free space in your assumed Fedora partition (/dev/sda6)[/indent]

Notes:
[indent]-> Gparted will not commit any changes until you click the final "Apply Changes" button. So you can make changes to your heart's content, undo/redo until you are satisfied. Then, and only when you are absolutely certain, click "Apply Changes" to carry out all your changes. Canceling the procedure anytime before clicking "Apply Changes" is absolutely safe and OK.

-> /dev/sda2 will not be displayed in the graphical bar view; rather it will be represented as an "outline" around /dev/sda5-7. You can choose /dev/sda2 from the table below, or by clicking the "outline"

-> Leave at least one swap partition active for the entire gparted procedure (Eg, do not "swapoff" both swap partitions)[/indent]

Here are some semi-specific instructions to increase space in your Windows partition /dev/sda1. All instructions have an inherent risk of data loss, so you do this at your own risk, sorry. I suggest you wait for someone else to approve the steps below before you actually do anything, in case I make a mistake in the instructions.

[indent]-> Ensure that neither of your 3 OSs are "hibernated".

-> Boot off an Ubuntu 9.04 live CD. (In 9.10, the partitioning tool changes).

-> Unless you have a specific need, there is no need to maintain different swap partition for Fedora and Ubuntu. If you are hibernating both OSs simultaneously, then you can consider having 2 swaps, else you should get rid of any one. Instructions on this will follow further below.

-> Press Alt+F2 and open gparted with the command```
gksudo gparted
```

-> EXCEPT for entries marked "swap", right-click all partition table entries that have a "lock" icon next to them, and choose "Unmount". (You can skip this if no entries have a "lock" icon).

-> If you decide to get rid of any one swap space (not both), then right click any one and click "Swapoff" (I suggest /dev/sda7). Then right click it and choose "Delete" to delete the swap partition (You can skip this entire step if you wish to retain two swap partitions).

-> Right click your /dev/sda6 partition, and choose "Shrink".

-> Reduce it's size as you feel suitable. Use the "handles" on either end of the space graph to reduce the size. Also choose to move the partition (Put free space to the left (/beginning) of the partition, closer to /dev/sda1/5). 

-> At this point, gparted should show, in order, /dev/sda1, /dev/sda2, /dev/sda5, Unpartitioned space, /dev/sda6 (Assumed Fedora), etc.

-> Right click and Move your /dev/sda5 partition into the free space before /dev/sda6 (Choose Resize/Move option).

-> At this point, gparted should show, in order, /dev/sda1, /dev/sda2, [color=blue]Unpartitioned space, /dev/sda5, /dev/sda6 (Assumed Fedora)[/color], etc.

-> Right click your /dev/sda2 partition and shrink it so that it matches the start of the /dev/sda5 partition (ie, effectively moving the unpartitioned space out of /dev/sda2 and next to /dev/sda1.

-> At this point, gparted should show, in order, /dev/sda1, [color=blue]Unpartitioned space, /dev/sda2,[/color] /dev/sda5, /dev/sda6 (Assumed Fedora), etc. The "Unpartitioned space" should be outside the "outline" of /dev/sda2.

-> Expand /dev/sda1 to the limit of the unpartitioned space (Eg next to /dev/sda2).

-> At this point, you are done, but no changes have been committed yet. If you have any doubts, please take a screenshot of the gparted screen and post it here for confirmation. If you are certain about the changes to be made, click "Apply Changes".

-> If you "Apply Changes", gparted will run for a long time moving data and partitions around. 15~20 hours is not uncommon. Canceling and/or interrupting the operation will most definitely cause loss of possibly all data. Please ensure adequate power backup. 
[/indent]

If all goes well, you should now have more free space in your Windows partition.

Note that all operations are at your own risk, I'm sorry to advise. 

If my assumptions are incorrect, or your requirements different, please post back.

[color=red]**A final note: I advise you not to go through with this procedure. In your shoes, I would not. The potential for data loss is too high. I would suggest you find some other way to free up space in your Windows partition.**[/color]

Please post back with specifics if you need more help.

---

### Post by astrobob.tk on 2009-12-17
> You have probably skipped one line of the fdisk output, something about "Partition table entries are not in disk order".i suppose not. this is it again:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23a323a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1657    13309821    7  HPFS/NTFS
/dev/sda2            1658        6756    40957717+   f  W95 Ext'd (LBA)
/dev/sda3            6757        9434    21504000   83  Linux
/dev/sda4            9434        9729     2376622+  82  Linux swap / Solaris
/dev/sda5            1658        3314    13309821    7  HPFS/NTFS
/dev/sda6            3315        6475    25390701   83  Linux
/dev/sda7            6476        6756     2257101   82  Linux swap / Solaris
```> Assumptions (Please correct if wrong, instructions will change):[INDENT] -> /dev/sda3 & 4 are related to your Ubuntu installation and /dev/sda6 & 7 (within the secondary partition) are related to your Fedora installation.

-> You want to increase space in /dev/sda1 Windows partition, not /dev/sda5 (within the secondary partition)

-> You have available free space in your assumed Fedora partition (/dev/sda6)[/INDENT]Well to be honest i dont not quite remember about, but I suppose after reviewing the table from GParted that the you flipped the partitions. Instead Ubuntu is on sda6 with the swap sda7 & i know thi since it has less unused space from the other partition (i.e.; sda3 & sda4 which might be the fedora i am not using).
here's a snapshot:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=5362[/IMG]

Well i think I will stick to what i currently have at least until i have time to rethink & do it. 

Anyways, I really appreciate your help & explanations :D

If in the future I consider taking such actions I will get back. I think I have to expand my HDD hehe.

one last thing. You mentioned early in ur post: > OK this is a sweet little nightmare of a setup.why is that ? & how do you suggest 2 or 3 OS's be setup ?

Thanks

---

### Post by prshah on 2009-12-18
> **astrobob.tk said:**
> i suppose not. 

here's a snapshot:

Well i think I will stick to what i currently have at least until i have time to rethink & do it. 

how do you suggest 2 or 3 OS's be setup ?


I don't mean that there is anything wrong with your OS setup; but (I guess) since you have been installing them at different times, the partition structure has become "fragmented" (for want of a better word), ie, your Linux and Windows partitions have become interspersed with each other, making consolidation or resizing of partitions a difficult operation. There is no effect to stability or performance. It's just difficult to alter.

As an example, in a dual-boot system, I would place Windows and swap partitions as "primary" partitions, and linux partitions inside an "extended" / secondary partition. It's a convention I follow, not a rule. The "/" partition does not usually cross over 7~9GB in size, so that comes first, and then a "/home" partition will swallow whatever diskspace is left. This way, when I expand to a bigger drive, I can dump the entire structure onto it, then simply expand the extended and the last "/home" to fill up the free space. 

Your snapshot has not come through; just FYI.

About a while back, I was running out of "/" space on my aging 40GB laptop; I reduced the size of the windows partition and extended/moved my "/" to take up the free space. However, my Windows partition also did not have much space; I followed the tips in [Tips : Reduce Size Of Windows Folder]("http://technical-issues-tips.blogspot.com/2007/08/tips-reduce-size-of-windows-folder.html") to regain a stunning 8GB; 5GB of which I then allocated to my "/". Maybe you could follow the same tips to create space on your Windows partition.

---

### Post by astrobob.tk on 2010-07-06
> **prshah said:**
>  As an example, in a dual-boot system, I would place Windows and swap partitions as "primary" partitions, and linux partitions inside an "extended" / secondary partition. It's a convention I follow, not a rule. The "/" partition does not usually cross over 7~9GB in size, so that comes first, and then a "/home" partition will swallow whatever diskspace is left. This way, when I expand to a bigger drive, I can dump the entire structure onto it, then simply expand the extended and the last "/home" to fill up the free space. 

About a while back, I was running out of "/" space on my aging 40GB laptop; I reduced the size of the windows partition and extended/moved my "/" to take up the free space. However, my Windows partition also did not have much space; I followed the tips in [Tips : Reduce Size Of Windows Folder]("http://technical-issues-tips.blogspot.com/2007/08/tips-reduce-size-of-windows-folder.html") to regain a stunning 8GB; 5GB of which I then allocated to my "/". Maybe you could follow the same tips to create space on your Windows partition.

Here's how I recently partitioned the disk:

```
Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       10499       10499           0   65  Novell Netware  386
Partition 3 does not end on cylinder boundary.
/dev/sdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

Do you think this is better ? or ?

---

