---
title: "Partition Table Help - Cannot have overlapping partitions"
date: 2010-09-26
forum: General Help
---

### Post by TheRussMan on 2010-09-26
Hi

I'm trying to increase the size of my ubuntu partition.  To do this I shrunk my windows partition using partitionmanager and then booted into an ubuntu livecd and tried to use gparted to add the unallocated space to my ubuntu partition.  Gparted showed my drive as unallocated and after some research I think this is because I have overlapping partitions.

sudo fdisk -l
Error: Cannot have overlapping partitions.

sudo sfdisk -l

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   7030-   7031-  56473168+   7  HPFS/NTFS
        end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda2      11548+  14592-   3045-  24456713    5  Extended
        start: (c,h,s) expected (1023,254,63) found (1023,236,27)
        end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      11548+  14461-   2914-  23401472   83  Linux
/dev/sda6      14461+  14593-    132-   1056768   82  Linux swap / Solaris

sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=112946337, Id= 7, bootable
/dev/sda2 : start=185522174, size= 48913426, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=185522176, size= 46802944, Id=83
/dev/sda6 : start=232327168, size=  2113536, Id=82


sda1 currently has windows (i'm in the process of getting rid of it, but needed more space on my ubuntu one first to copy things across)
sda5 is Ubuntu

How do I go about resolving the overlapping partitions so I can use gparted to resize sda5 and also do I need sda1 to be bootable, I believe that grub is on sda5, so can I make that bootable instead ready for when I finally remove sda1?

Thanks

---

### Post by TheRussMan on 2010-09-26
Bump.

I don't suppose anyone can help?

---

### Post by srs5694 on 2010-09-26
I don't see anything wrong with those partitions; however, it's very difficult to parse because you posted it without using [noparse]```
[/noparse] and [noparse]
```[/noparse] tags before and after the output. This corrupts the columnar output of these programs. Also, one critical piece of data is missing: The size of the disk in sectors. (The size in cylinders isn't precise enough.)

Usually, fdisk will display disk data even if it detects corruption, so the refusal to do so in your case is puzzling. I have a sneaking suspicion you may be using [GNU fdisk,](http://www.gnu.org/software/fdisk/) which is based on libparted, which tends to be very fussy and inflexible about such things. I recommend you remove the gnu-fdisk package, ensure that the util-linux package is installed, and try again, but this type use "sudo fdisk -lu" and be sure to use the [noparse]```
[/noparse] and [noparse]
```[/noparse] tags.

Also, you may want to check [this Web page](http://www.rodsbooks.com/missing-parts/index.html) that I wrote about such problems. I don't see evidence of the specific problem described on the Web page in your output, but the data are incomplete. "sudo fdisk -lu" using the fdisk from util-linux should produce the required output.

---

### Post by Quackers on 2010-09-26
Which Windows version are you using?

---

### Post by TheRussMan on 2010-09-26
> **srs5694 said:**
> 

Hi, you're quite right about the gnu-fdisk and now I've removed it I get following output:

 ```
 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x64656469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   112946399    56473168+   7  HPFS/NTFS
/dev/sda2       185522174   234435599    24456713    5  Extended
/dev/sda5       185522176   232325119    23401472   83  Linux
/dev/sda6       232327168   234440703     1056768   82  Linux swap / Solaris


```

Thanks for the assistance so far.


And @Quackers I'm using Windows XP.

---

### Post by Quackers on 2010-09-26
One question that occurs to me from your last post. Does your extended partition include sda2 and sda5? If so, why don't they start on the same sector? Maybe they shouldn't, I'm not really sure.

---

### Post by TheRussMan on 2010-09-26
> **Quackers said:**
> One question that occurs to me from your last post. Does your extended partition include sda2 and sda5? If so, why don't they start on the same sector? Maybe they shouldn't, I'm not really sure.

Hmm, that might be right because if you look at the cylinders the extended partition starts on the same value as sda5.  Although I assume it should end with the same value as sda6 as sda2 included sda5 and sda6.  Do you know where I could check?

```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x64656469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7470    56473168+   7  HPFS/NTFS
/dev/sda2           12270       15505    24456713    5  Extended
/dev/sda5           12270       15366    23401472   83  Linux
/dev/sda6           15366       15506     1056768   82  Linux swap / Solaris



```

---

### Post by Quackers on 2010-09-26
I'm really not sure, I'm afraid.
Can you post a screenshot of what Gparted shows for the partition structure?

---

### Post by TheRussMan on 2010-09-26
> **Quackers said:**
> I'm really not sure, I'm afraid.
Can you post a screenshot of what Gparted shows for the partition structure?

Here we go, but as you can see it doesn't show anything because of the overlapping partitions.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=170599&stc=1&d=1285534498[/IMG]

---

### Post by Quackers on 2010-09-26
Oh, I see. I'm sorry I wasted your time there. You already said that - my bad.
Try downloading and running the boot info script from this link and posts the results in code tags, as before.
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

We could do with srs5694 coming back. He knows his stuff.

---

### Post by TheRussMan on 2010-09-26
I've run the boot script but as the results are quite long I've attached it rather than pasted it in.

I'm assuming the issue is something to do with the line at the bottom of this

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   112,946,399   112,946,337   7 HPFS/NTFS
/dev/sda2         185,522,174   234,435,599    48,913,426   5 Extended
/dev/sda5         185,522,176   232,325,119    46,802,944  83 Linux
/dev/sda6         232,327,168   234,440,703     2,113,536  82 Linux swap / Solaris

the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2


```

Assuming that isn't normal.

---

### Post by Quackers on 2010-09-26
If you enclose it in the code tags it will shorten the output and create a scroll bar.
According to the boot script the number of sectors taken by sda1 (windows) seems to be disputed, 
ie 
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       112936872 sectors, but according to the info from 
                       fdisk, it has 112946336 sectors.

Also, it reads as though the only thing on sda2 is an unknown bootloader. Do you know anything about that?
I'll keep looking and get back to you.

---

### Post by Quackers on 2010-09-26
The only thing I can think of that may resolve the issue with sda1 sectors is to increase (or decrease) the partition size - say by 100MB or something like that. But I would do it with the GParted Live cd (not the version that comes with Ubuntu). (If the live cd can read the partition info and mount the drive ok).
If that works at least we will know that sda1 is ok.
If you would rather wait until somebody else comes online (more will be on soon, I'm sure - in different time zones) who has more experience in these matters than I do, I wouldn't blame you :-)
Best of luck to you. I'll keep thinking in the meantime!

---

### Post by TheRussMan on 2010-09-26
> **Quackers said:**
> The only thing I can think of that may resolve the issue with sda1 sectors is to increase (or decrease) the partition size - say by 100MB or something like that. But I would do it with the GParted Live cd (not the version that comes with Ubuntu). (If the live cd can read the partition info and mount the drive ok).
If that works at least we will know that sda1 is ok.
If you would rather wait until somebody else comes online (more will be on soon, I'm sure - in different time zones) who has more experience in these matters than I do, I wouldn't blame you :-)
Best of luck to you. I'll keep thinking in the meantime!

Thanks for the advice, unfortunately gparted has the same issue on the live cd as well, it obviously doesn't like something to do with my partition :(.

---

### Post by Quackers on 2010-09-26
I meant the GParted Live CD, not the Ubuntu Live Cd. Did you try that too?
The advice is not a problem. I have had pleeeeeeeeeenty from others on here. I'm just sorry we can't solve it yet.

---

### Post by srs5694 on 2010-09-27
The problem is that /dev/sda6 runs from sector 232,327,168 to 234,440,703, but /dev/sda2 (which is supposed to contain both /dev/sda5 and /dev/sda6) ends at sector 234,435,599 -- 5,104 sectors too early! There are several possible solutions, but the easiest and safest is probably this:


[list=1]
[*]Disable swap space. Typing "sudo swapoff -a" should do this.
[*]Enter fdisk and use it to delete /dev/sda6. (Type "d" and enter "6" as the partition number.)
[*]Type "w" in fdisk to save your changes.
[*]Reboot.
[*]Use GParted to create a new swap partition.
[*]Edit /etc/fstab and change the UUID number for your swap space to match the new swap space created by GParted. (Use the blkid text-mode tool to find the UUID number, as in "sudo blkid /dev/sda6".)
[/list]


This procedure will get you back to a working state equivalent to what you've got now. Since you're repartitioning anyway, you may want to interleave whatever other operations you had planned in there, once you get to the point that GParted is working on the disk. Alternatively, you could do some of it in fdisk, if you prefer.

---

### Post by TheRussMan on 2010-09-27
> **srs5694 said:**
> The problem is that /dev/sda6 runs from sector 232,327,168 to 234,440,703, but /dev/sda2 (which is supposed to contain both /dev/sda5 and /dev/sda6) ends at sector 234,435,599 -- 5,104 sectors too early! There are several possible solutions, but the easiest and safest is probably this:


[LIST=1]
[*]Disable swap space. Typing "sudo swapoff -a" should do this.
[*]Enter fdisk and use it to delete /dev/sda6. (Type "d" and enter "6" as the partition number.)
[*]Type "w" in fdisk to save your changes.
[*]Reboot.
[*]Use GParted to create a new swap partition.
[*]Edit /etc/fstab and change the UUID number for your swap space to match the new swap space created by GParted. (Use the blkid text-mode tool to find the UUID number, as in "sudo blkid /dev/sda6".)
[/LIST]


This procedure will get you back to a working state equivalent to what you've got now. Since you're repartitioning anyway, you may want to interleave whatever other operations you had planned in there, once you get to the point that GParted is working on the disk. Alternatively, you could do some of it in fdisk, if you prefer.

That's amazing.  I've done all of that and it all seemed to work brilliantly.  GParted works and I've resized the partition, created a new swap and added the UUID into fstab and remounted.  I'm guessing the swap drive is now functional.  Is there a way to check it?  Also I wasn't sure of the size, so went for 2gb.

One last question if that's ok, at the moment I believe I have GRUB on sda5, but sda1 is listed as the boot partition.  As I want to delete this eventually, can I just change it to sda5, or will I need to do some configuration?

Thanks again for all your help.

---

### Post by srs5694 on 2010-09-27
Type "swapon -s" to see a summary of swap space use. If the swap partition is listed, then it's being used; if not, then there's a problem with the /etc/fstab entry. (Assuming you've rebooted; if you haven't, you'll need to type "swapon -a" or reboot to activate the swap space defined in /etc/fstab.)

GRUB ignores the boot/active flag in the MBR, so deleting /dev/sda1 won't cause any problems. (Unless you've got GRUB configuration files there or are using some Windows boot loader to chain-load GRUB.)

---

### Post by TheRussMan on 2010-09-28
> **srs5694 said:**
> Type "swapon -s" to see a summary of swap space use. If the swap partition is listed, then it's being used; if not, then there's a problem with the /etc/fstab entry. (Assuming you've rebooted; if you haven't, you'll need to type "swapon -a" or reboot to activate the swap space defined in /etc/fstab.)

GRUB ignores the boot/active flag in the MBR, so deleting /dev/sda1 won't cause any problems. (Unless you've got GRUB configuration files there or are using some Windows boot loader to chain-load GRUB.)

Perfect.  Thanks very much for your help.

---

### Post by Quackers on 2010-09-28
Very nice. He knows, you know!

---

