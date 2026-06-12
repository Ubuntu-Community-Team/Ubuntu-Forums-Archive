---
title: "keys: press S to skip mounting?"
date: 2011-02-13
forum: General Help
---

### Post by garyed on 2011-02-13
I get this message at boot up:

> keys: Press S to skip mounting or M for manual recovery

If I press "S" it usually boots O.K. but not always but if I press M or nothing it doesn't boot at all. 

I removed some drives from fstab & that seemed to help for about a week or two but now it does it again & more often. I trimmed fstab to where there's nothing but \ , swap, & \home & still the same problem. The one thing that I've noticed is that my 4 hard drives are changing without any changes being made in the bios. For instance my last boot:
fdisk -l showed 
> sda1     NTFS Drive
       sdb1-7  Linux Gusty & Lucid
       sdc1    Fat32 Drive
       sdd 1  Puppy Linux 
 
 
This boot fdisk -l shows: 
       sdc1     NTFS Drive
       sdd1-7  Linux Gusty & Lucid
       sda1    Fat32 Drive
       sdb 1  Puppy Linux 
   
I have two IDE drives & two SATA drives which may be the problem. 
Does anybody have any ideas?

---

### Post by dabl on 2011-02-13
I'm not sure how many problems you have there.  The one concerning "randomly changing device IDs" can be completely resolved by using "mount by-UUID" in /etc/fstab, in lieu of "mount by /dev/sdXY". In other words a line in /etc/fstab should look approximately like this:

```
UUID=82fffe8d-a8b1-49f7-afce-6ff01bc544bf     /mnt/WHATEVER        ext4         auto,users,rw,exec,noatime    0    0
```

not this:

```
/dev/sdb1     /mnt/WHATEVER        ext4         auto,users,rw,exec,noatime   0    0
```

---

### Post by garyed on 2011-02-13
Thanks for the ideas but I'm sorry to say that fstab is already using uuid's & I still have the problem.
Here's what it looks like:

```

cat /etc/fstab
 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd6 during installation
UUID=9491c0ca-97d5-4b39-819a-671b97879dbe /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd7 during installation
UUID=08258798-0555-42b1-80af-cacb43f99c0c /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=d2f0f089-7888-41be-8a33-7123fab40f40 none            swap    sw              0       0
  
# /dev/sdd1      /media/gusty      ext3    defaults   0        0                      
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0




```
I tried commenting out the floppy line too but that didn't help either.

---

### Post by dabl on 2011-02-13
OK the two ext4 partitions look fine -- I see the commented out Gutsy partition which was _not_ mounted with the UUID -- not sure what happened to the rest of the other partitions.

Another potential issue that could generate the "Press S ..." is, when was the last time you fsck'd those partitions?  Unfortunately with the default "quiet" boot option, the fscks are now hiding during the boot process and the temptation is to skip them -- but there's a reason fsck exists.

Do you have a Live CD or USB stick that has GParted or partitionmanager on it?  Personally I like the Parted Magic Live CD, but Ubuntu Live CD will work too.  Trying running GParted, right-click on the graphic for each partition on your drives, and choose "check", then choose "Apply" on the top menu.

(Of course you could also, from a Live CD session, open a terminal and issue ```
sudo e2fsck -vp /dev/sdd6
``` to fsck that partition.)

Afterwards, reboot and see if you get a better result.

---

### Post by garyed on 2011-02-13
> **dabl said:**
> .......

(Of course you could also, from a Live CD session, open a terminal and issue ```
sudo e2fsck -vp /dev/sdd6
``` to fsck that partition.)

Afterwards, reboot and see if you get a better result.

I booted with a live CD & ran that command, it said the partition was "clean".
Rebooted & the same problem.
I'm starting to think it might have something to do with Grub2 now.
I'm booting Ubuntu 10.04, Ubuntu 7.10 , Windows XP & Puppy Linux. 
Ubuntu 7.10 is on the same drive as 10.04 & it boots fine, so do all the other OS's. The only problem one is 10.04.

---

### Post by dabl on 2011-02-14
The reference to "mounting", and the fact that it occurs during the boot process, makes me think it is all about /etc/fstab.  If it were a grub problem, grub has its own obscure little error outputs.

However, you might want to take a peek at the file /boot/grub/device.map in case you see anything that looks "wrong" there.

---

### Post by arsenic23 on 2011-02-14
Another thought:  Is SMART detection enabled in your bios?  Could is be possible one or more of your drives is going south?

---

### Post by garyed on 2011-02-14
> **arsenic23 said:**
> Another thought:  Is SMART detection enabled in your bios?  Could is be possible one or more of your drives is going south?
I have a setting for my IDE drives called "smart monitoring" I tried disabled & enabled but either way it didn't make a difference. 
One more thing is if I press the second option "M" for manual recovery it takes me to a command prompt that says:
> 
Invalid GART PTE entry during tablewalk.
File system check or mount failed.
...... press Ctrl-d to return

Ctrl-d returns me to the screen where I can press "S" to skip mounting & it boots fine again. Once in a while it still hangs after pressing "S" but only rarely.
I did some googling & there are some bugs reported with those errors & an Asus MB which is what I have. I'm not sure if my problem is the same but it only does it when booting into these two kernels:
>  vmlinuz-2.6.32-21-preempt  or  vmlinuz-2.6.32-28-preempt          

By the way I'm booting into Ubuntu Studio 10.04 when this happens.
I've got four HD's -  2- SATA  &  2-IDE.  My slave IDE is where 10.04 is located.

---

### Post by dabl on 2011-02-14
> **garyed said:**
> 
One more thing is if I press the second option "M" for manual recovery it takes me to a command prompt that says:

Ctrl-d returns me to the screen where I can press "S" to skip mounting & it boots fine again. Once in a while it still hangs after pressing "S" but only rarely.


Ahhhhhh.  Let's see the output of

```
sudo fdisk -lu
```

please.

---

### Post by garyed on 2011-02-14
> **dabl said:**
> Ahhhhhh.  Let's see the output of

```
sudo fdisk -lu
```

please.

Here it is:
> 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92c092c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aec26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   105482789    52741363+  83  Linux
/dev/sdb2       105482790  1953520064   924018637+   5  Extended
/dev/sdb5       105482853   778172534   336344841   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92819281

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005598e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    97659134    48829536   83  Linux
/dev/sdd2        97659259   312576704   107458723    5  Extended
/dev/sdd5       307451970   312576704     2562367+  82  Linux swap / Solaris
/dev/sdd6        97659261   128375414    15358077   83  Linux
/dev/sdd7       128375478   307451969    89538246   83  Linux

Partition table entries are not in disk order
gary@ustudio104:~$ 




---

### Post by dabl on 2011-02-15
> **garyed said:**
> 
Partition table entries are not in disk order

Depending on the sequence in which you did partitioning/repartitioning and installation of your OS and Grub, I would guess this is behind the boot error that you are seeing.

---

### Post by garyed on 2011-02-15
> **dabl said:**
> Depending on the sequence in which you did partitioning/repartitioning and installation of your OS and Grub, I would guess this is behind the boot error that you are seeing.

You could be right but I have no idea how to fix it.
I know that sdc is the primary ide boot disk in my bios & sda is the slave.
The boot order in the bios is IDE & then SATA drives.

---

### Post by dabl on 2011-02-15
Can you post the contents of /boot/grub/device.map?

---

### Post by garyed on 2011-02-15
> **dabl said:**
> Can you post the contents of /boot/grub/device.map?
I didn't think grub2 had a device.map.
Is it in some other file name?

---

### Post by dabl on 2011-02-16
Hmmmmm.  I think you're right, more or less.  My other Debian system has one, but it doesn't have any drives listed in it.  The one I posted from does have /boot/grub/device.map with partitions listed, but now that I think about it, it was once a legacy grub booter, so that's why.

Never mind ...

---

### Post by garyed on 2011-02-16
A little update:

I copied my whole problem partition where my OS(U-Lucid-Studio) is to another drive, reinstalled grub & made some changes to fstab & grub.cfg etc.. & it booted with the same problem from the new drive location. I then reformatted that partition I just copied the OS to & booted a live CD & installed Lucid there. The new installation of Lucid boots fine. Since plain Lucid works fine & Lucid Studio does not I'm wondering if its something in the kernel thats making a difference. They both work fine once I get them booted. fstab's are very similar except different root partitions. 
I may just try a new install on the partition thats having the problem & see if anything changes but I doubt it.

---

### Post by dabl on 2011-02-16
Another experiment you could try is with a downloaded 11.04 daily build.  "They" say that the new 2.6.37 and 2.6.38 kernels are so fast that the separate RT spin will not be necessary to reduce latency.  I can't confirm that, but it would be interesting to hear how it works.  I have 11.04 Kubuntu on a VM and it seems fine although I wouldn't trust it with serious productivity work at this point.

---

### Post by yoni_m on 2011-07-07
Hi,
I might be completely of track but I had the same problem and this link:
[http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/]("http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/")
pointed me in the correct direction.

My problem was that the numbers in the
/etc/fstab
file did not match the ones given by 
ls -l /dev/disk/by-uuid

I copied the nubers (e.g. 78B89FDAB89F956A) to the correct dev in the fstab file.

My problem was created after I reinstated win7 so the uuid for the partition was changed but ubuntu and the grub did not know about this.

Good luck.

---

