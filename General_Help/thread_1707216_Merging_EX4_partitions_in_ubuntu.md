---
title: "Merging EX4 partitions in ubuntu"
date: 2011-03-15
forum: General Help
---

### Post by Mamadex on 2011-03-15
Hello 

I have 3 Linux partitions for ubuntu:[INDENT][COLOR=DimGray]1. NTFS (used for win xp)[/COLOR]
2. first : **\**
3. second : mount at **\var** (chosen at the installation of ubuntu)
4. third : **swap**
[/INDENT]**now how do I merge Linux directories (2,3 partitions only) without losing data?**

note that the all listed partitions above are located in extended area, Primary partitions is NTFS and only contains win 7. (I have 3 OS :D) here's summary of hard disk:
> Primary:
---      NTFS [COLOR=Silver](win 7)[/COLOR]
Extended:
--- NTFS [COLOR=Silver](win xp)[/COLOR]
---      Ext4 [COLOR=Silver](\)[/COLOR]
---      Ext4 [COLOR=Silver](\var)[/COLOR]
---      swap
And this is image of partitions:
[IMG]http://ubuntuforums.org/editpost.php?do=updatepost&postid=10561446[/IMG]

---

### Post by Mamadex on 2011-03-15
some tips:
- we can unmount partition **\var** but then what's happen? I think partition will lose.
- I we copy **\var** in **\** then do we have a logical folder which work correctly. by this we should delete **\var** partition. Will Linux works good then?
- What if we merge partitions in windows using a *Partition Manager Software* like [Paragon]("http://www.paragon-software.com/")? I think this will not goes nice! (Paragon supports merging Linux partitions.)

so, any comment?!

---

### Post by Mamadex on 2011-03-15
I really need help, please.

---

### Post by plucky on 2011-03-15
> **Mamadex said:**
> I really need help, please.

I don't think I have seen a HOWto merge a system partition back into the /root partition is possibly the reason you are not getting any replies.

If I were you,I would backup your data in the /home area in the linux install and then delete both the / and /var partitions and re-install to one / partition, that you create in the now un-allocated space, as the size is only 20Gb.Then copy your data back into the /home space.

What are you planning for the 42Gb partition that is un-used at the start of the disk?

Why did you create a separate /var partition?

Good Luck

---

### Post by Mamadex on 2011-03-15
> **plucky said:**
> 

Why did you create a separate /var partition?
because I accept suggestion to have separate partitions, one for *archive* folder located at : */var/cache/apt/archives* which have ubuntu download packs. I am absolutely remorseful to did this. :confused:

---

### Post by rubylaser on 2011-03-15
You could do this from the livecd.  You'd need to mount your two partitions, and then rsync everything from your current /var partition over into your / partition (into a folder called var).  Then, you'd want to edit your /etc/fstab file and comment out the line that mounts the second partition on /var.  Reboot, without the livecd, and verify that your system is still functional (if not, you can still easily roll back at this point by uncommenting the /var  line /etc/fstab).  

If all is well, you can reboot and run for the live gparted cd, and delete your unnecessary partition and extend your current /.  I can not stress strongly enough, you will want to **BACKUP** before you try any of this.

---

### Post by Mamadex on 2011-03-15
> **rubylaser said:**
> You could do this from the livecd.  You'd need to mount your two partitions, and then rsync everything from your current /var partition over into your / partition (into a folder called var).  Then, you'd want to edit your /etc/fstab file and comment out the line that mounts the second partition on /var.  Reboot, without the livecd, and verify that your system is still functional (if not, you can still easily roll back at this point by uncommenting the /var  line /etc/fstab).  

If all is well, you can reboot and run for the live gparted cd, and delete your unnecessary partition and extend your current /.  I can not stress strongly enough, you will want to **BACKUP** before you try any of this.

Thank you

by Replacing files from [**/var partition]** to [**/ partition] **in* var* folder, and setting /etc/fstab up, done.
now if I use Gparted to *delete the 5 Gigs partition* then *resizing **\** partition with livecd*, is everything ok?
I did it before complete applying It said something like "Are you sure, editing partitions may loss data" !

please help, again.

---

### Post by rubylaser on 2011-03-15
Yes this should work, but again, I hope you've made a backup of your critical data.  Editing partitions can remove data, so that's a good warning.  You should be able to proceed if you've made your backup.

---

### Post by sedawk on 2011-03-15
Some general comments:

Very often with Ubuntu, people do not have anything vital
outside the /home folder.
So after a backup of /home it might be the easiest way
to modify the partition table and install Ubuntu from
scratch.
This obviously is not the right solution if you added
additional software that is not part of Ubuntus base system.

If there is important stuff on a disk (e.g dual boot, etc)
I recommend a full backup before touching the partitioning.
E.g with a tool like partimage and an external disk.
(better: two external disks!)

Actually it is not a bad idea to have /var on a separate
partition. The "/var" filesystem is a growing file system
containing log files, the "/var/tmp" directory and some
mail folders.
Running out of disk space can be a frustrating experience
and therefore on "real" servers you will see that /var
and /var/tmp are mounted to separate file systems.

---

### Post by Mamadex on 2011-03-15
> **rubylaser said:**
> Yes this should work, but again, I hope you've made a backup of your critical data.  Editing partitions can remove data, so that's a good warning.  You should be able to proceed if you've made your backup.

how about using Partition Manger software in windows that suports resizing Linux partitions?
or you prefer me to using GParted in livecd?

Note that with gparted (for the swap partition) we must swap-off first. Set changes to partitions, finally swap-on.

---

### Post by rubylaser on 2011-03-15
I would use gparted.

---

### Post by Mamadex on 2011-03-16
That confirmation message of Gparted was bad for me!

> **rubylaser said:**
> I would use gparted.
I see your message [COLOR=Gray](using Gparted)[/COLOR] after I made the partitions damaged. :(
To merging partitions I used P*aragon Partition Manger* in windows. merged successfully, but now I can't boot to Ubuntu.
**How can I solve this?**
there are the boot options at the start-up but choosing Ubuntu shows message something like "bad partition" then goes to >Grup command-line window!
note that *Paragon* still tells everything is OK even shows **\** partition's data (by using its internal browsing explorer).
I can't restore back changes that I've done.
the livecd disk-utility application tells "160G Unallocated Disk" !!!

Please help.

---

### Post by Mamadex on 2011-03-16
Even now I can't install Ubuntu in the partition which is already resized.
everything is gone. only an unallocated partition is!
*rubylaser* what's solution to this problem? I've lost ext4 partitions.

---

### Post by rubylaser on 2011-03-16
You need to use gparted, that's why I suggested it.  I've never used Paragon's tool, so I can't tell you what it did wrong.  The easiest thing to do would be to reinstall and restore from the backups that I'm sure you made.

If not, you'll need to use the fdisk to change the partition label, but I don't know how to tell you to proceed, because I have no idea what that tool did.  Can you post the output this of from the livecd...
```
fdisk -l
```

---

### Post by Mamadex on 2011-03-16
Because there were no partition showing by the Ubuntu installer I go to Windows>Disk Management and delete EXT4 Partition. Sudenly the blue screen occurs and computer restarted. by this the extended partition removed (containing XP and Ubuntu and swap). but Primary partition exist sill (win 7). I ran Paragon tool and recover extended-NTFS (XP) partition.
Then I install Ubuntu using livecd.
> fdisk -l
the code does show nothing in terminal (of new Ubuntu).

now I have new Ubuntu OS. This is not good, I got backup of */home* and */var/cache/apt/archives* but my settings has been lost!

Thanks for communicating.

---

### Post by rubylaser on 2011-03-16
Well you only have a partial backup then... You need to be superuser to use fdisk, so

```
sudo fdisk -l
```

At this point, you've removed your EXT4 partition, so there's not really anything to be done to recover your settings since you deleted the filesystem.

---

### Post by Mamadex on 2011-03-16
> **rubylaser said:**
> Well you only have a partial backup then... You need to be superuser to use fdisk, so

```
sudo fdisk -l
```At this point, you've removed your EXT4 partition, so there's not really anything to be done to recover your settings since you deleted the filesystem.

I install new Ubuntu.
anyway this is hard-disk new partitions info:

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xccdf0203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        5100       11473    51199123+   7  HPFS/NTFS
/dev/sda2           11474       19458    64133145    f  W95 Ext'd (LBA)
/dev/sda5           11474       16704    42017976    7  HPFS/NTFS
/dev/sda6           16705       19202    20063232   83  Linux
/dev/sda7           19202       19458     2050048   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd04154b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    7  HPFS/NTFS
But I don't know what was in that time. It's so funny that I forgot to enter one sudo word :confused:.

---

