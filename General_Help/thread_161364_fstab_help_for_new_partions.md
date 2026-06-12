---
title: "fstab help for new partions"
date: 2006-04-16
forum: General Help
---

### Post by vol_freak on 2006-04-16
I just copied my entire drive with all of my windows and linux partitions to a new and bigger drive using dd from the command line from a boot cd. Everything worked flawlessly except that I now need to reclaim the additional space from the new drive. I already have 4 primary partitions so I am unable to use it as is. 

my partitions are:
hda1 windows ntfs for xp
hda2 boot
hda3 main linux partition
hda4 swap

my idea was to delete the swap file and then create and extended partition that  would contain a swap partition and a fat partition to be used by linux and windows. I did all of that with no problem. Ubuntu would not fully boot.

I assume the problem is with my fstab. I tried editing it to just change the swap from hda4 to hda6 but I assume there is something I am missing becuase it did not work. 

Any suggestions?

---

### Post by aysiu on 2006-04-16
By what method did you try to edit /etc/fstab? What was the failure or error message?

---

### Post by vol_freak on 2006-04-16
No failure or errror message. I was able to edit the fstab but it still would not boot for some reason. I assumed that I am missing something to do with it being a logical partition and not a primary one. Does that matter? Or does the extended partition itself have to be mounted in addition to the logical partition of the swap file? I am grabbing at straws here.

---

### Post by aysiu on 2006-04-16
Typing ```
sudo fdisk -l
``` should tell you what your current partition table looks like.

---

### Post by vol_freak on 2006-04-16
to clarify the last post here is what my drive looks like:

hda1 ntfs
hda2 boot
hda3 linux
hda4 extended
hda5 fat32
hda6 swap

What I am asking is does the hda4 have to be mounted in some way and do I have to change anything in my fstab regarding hda6 being on a logical partition?

thanks

---

### Post by vol_freak on 2006-04-16
I changed everything back but right now it shows this:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3813    28826248+   7  HPFS/NTFS
/dev/hda2            3814        3817       30240   83  Linux
/dev/hda3            3818        4978     8777160   83  Linux
/dev/hda4            4979        5167     1428840   82  Linux swap / Solaris


afterwards I just changed the hda4 to hda6 and that was all I did.

---

### Post by aysiu on 2006-04-16
Maybe something like this: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /boot ext3    defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hd1        /windows   nls=utf8,umask=0222     0       0
```

---

### Post by vol_freak on 2006-04-16
That's basically what I have and it's not working. I don't know what else it could be. I change change the partitions back and it works. I try to add the new partitions and it won't load.

---

### Post by vol_freak on 2006-04-16
[QUOTE=vol_freak]That's basically what I have and it's not working. I don't know what else it could be. I change change the partitions back and it works. I try to add the new partitions and it won't load.[/QUOTE]


Hmm. I just recreated the paritions again and here is my fdisk -l. could it be a problem with the type of extended partition or does this look correct?

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3813    28826248+   7  HPFS/NTFS
/dev/hda2            3814        3817       30240   83  Linux
/dev/hda3            3818        4978     8777160   83  Linux
/dev/hda4            4979        7752    20971440    f  W95 Ext'd (LBA)
/dev/hda5            4979        7563    19542568+   b  W95 FAT32
/dev/hda6            7564        7752     1428808+  82  Linux swap / Solaris

---

### Post by aysiu on 2006-04-16
I think I may know a solution, but I'm not sure it'll work.

Here's my idea--let me know what you think.

Pop in the Ubuntu installer CD.
Choose to **Manually edit the partition table.**
Mount each partition as you want, but choose to format none of them.
I think it'll give you some kind of warning, but it may still let you proceed. Of course, I don't know if that'll create a new /etc/fstab for you...

---

### Post by vol_freak on 2006-04-16
[QUOTE=aysiu]I think I may know a solution, but I'm not sure it'll work.

Here's my idea--let me know what you think.

Pop in the Ubuntu installer CD.
Choose to **Manually edit the partition table.**
Mount each partition as you want, but choose to format none of them.
I think it'll give you some kind of warning, but it may still let you proceed. Of course, I don't know if that'll create a new /etc/fstab for you...[/QUOTE]
Interesting idea. I will try that now.

---

### Post by vol_freak on 2006-04-16
It did not create a new fstab unless I let it install everything else. 

I am really at a loss here.

---

### Post by vol_freak on 2006-04-17
I don't think it's an fstab issue now. I even booted to knoppix to take a look at that fstab. It has to be some other setting or config file somewhere. 

I put the partitions back the way it was and everything works fine but I am unable to use that extra space from my new hard drive.

---

### Post by Sutekh on 2006-04-17
I think you may have had a problem with the location of the swap space, which you already guessed.

Swap can be a logical partition in an extended partition, but I would think that it needs to be on a native Linux extended partition not a Windows 95 LBA one

```
/dev/hda4 4979 7752 20971440 **f** W95 Ext'd (LBA)
/dev/hda6 7564 7752 1428808+ 82 Linux swap / Solaris
```

Here's my partition setup```

/dev/sdb2            2433       30401   224660992+   **5**  Extended
/dev/sdb5           30024       30401     3036253+  82  Linux swap / Solaris

```
My swap /dev/sdb5 is on a Linux extended partition (type **5**) /dev/sdb2, yours is on a type **f** partition.

I have no idea how this happened, what did you use to partition your disc?

---

### Post by vol_freak on 2006-04-17
I thought that was it also since I had partioned that space with Partition Magic. I deleted the partition and re did it with gparted. No Luck. I even went a step farther and deleted that entire 4th partition and turned off swap all toghether and then all works fine. The second I add the extended partition, even if I don't allocate the space into any logical drives, it won't boot. So, what could Ubuntu not be liking about that extended partition. If I make it primary, no problem, but extended it won't get past the loading modules part at boot.

---

### Post by vol_freak on 2006-04-17
[QUOTE=vol_freak]I thought that was it also since I had partioned that space with Partition Magic. I deleted the partition and re did it with gparted. No Luck. I even went a step farther and deleted that entire 4th partition and turned off swap all toghether and then all works fine. The second I add the extended partition, even if I don't allocate the space into any logical drives, it won't boot. So, what could Ubuntu not be liking about that extended partition. If I make it primary, no problem, but extended it won't get past the loading modules part at boot.[/QUOTE]
Another addition. I decided to boot into recovery mode which I should have done a long time ago. 

I get:

attempt to access beyond end of device
hda4 rw=16 want=8 limit=16
kernel panic - not synching IO error reading memory image

It looks like it still thinks I have the smaller drive maybe?

---

### Post by vol_freak on 2006-04-17
Anyone have any other ideas? I am willing to try anything.

---

### Post by aysiu on 2006-04-17
[QUOTE=vol_freak]Anyone have any other ideas? I am willing to try anything.[/QUOTE] Even a reinstall...?

---

### Post by vol_freak on 2006-04-17
[QUOTE=aysiu]Even a reinstall...?[/QUOTE]
I suppose it may come down to a reinstall or trying to just resize my existing partitions. I know that there has to be a solution to this problem. Someone has surely run into this before. I just  have to hope they come along and see this thread.

---

### Post by jomtois on 2006-05-17
I got the same thing this morning when I did the same thing you did, made a logical partition (in gparted) and then tried to put the swap there....

did you ever find a solution???

I'm stuck at 

kernel panic - not synching IO error reading memory image

thanks
jon

---

### Post by jomtois on 2006-05-18
[QUOTE=vol_freak]Someone has surely run into this before. I just  have to hope they come along and see this thread.[/QUOTE]

Well, I was watching this thread and another, and hopefully what worked for me will work for you.  Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=159309]("http://www.ubuntuforums.org/showthread.php?t=159309")

Good luck!

---

