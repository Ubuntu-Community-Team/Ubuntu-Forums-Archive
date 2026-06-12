---
title: "Ubuntu reports low disk space - gparted doesn't"
date: 2010-07-24
forum: General Help
---

### Post by techrunner on 2010-07-24
Total Newbie running Win 7, Lucid Lynx 64-bit, sharing partition

Ubuntu keeps reporting low disk space. I've read dozens of postings, looked at gparted and done some resizing but it's still not right. Had to remove everything I could last night to free up space.

Disk utility shows I have an 18 GB root.disk, gparted shows partition has 204 GB available.

The space is there in the partition how do I get root size to increase?

attached gparted screenshot

Thanks!

---

### Post by neoargon on 2010-07-24
Where is the partition in which you installed ubuntu? I mean a partition with file system ext4?

---

### Post by Rubi1200 on 2010-07-24
From the terminal, can you post the output of

```
df -m
```

and

```
sudo fdisk -l
```

please

---

### Post by CharlesA on 2010-07-24
I don't see any / partition, so could you please run the commands that Rubi posted and post the output?

How did you install Ubuntu?

---

### Post by cgroza on 2010-07-24
It seems you installed using WUBI, i dont see any ext4 FS in there!

---

### Post by neoargon on 2010-07-24
You installed ubuntu inside windows ,didn't you? If yes,
When installing ubuntu, you set the size of ubuntu disk to "some size", in your case 18GB.  That size cannot be extended by providing more size in C drive. 
When installing inside windows, you are installing in a virtual drive and not in real drive . the size of that drive is the "some size " you given. 

Your problem might be a problem with windows boot loader. Try solving in that direction . Or install Ubuntu in a real drive .

Installing inside windows means you inserted the Ubuntu CD while you are running windows, followed the instructions of auto run prompt and installed ubuntu.

---

### Post by techrunner on 2010-07-24
I did do a dual boot install from windows and retained disk format.
 
If I can't increase the size is it possible to do a backup, reinstall in a new partition, and then restore? I have done a lot of setup over the past several weeks and would prefer not to have to redo it all.

Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/loop0               16481      8232      7412  53% /
none                      1897         1      1897   1% /dev
none                      1902         1      1901   1% /dev/shm
none                      1902         1      1902   1% /var/run
none                      1902         0      1902   0% /var/lock
none                      1902         0      1902   0% /lib/init/rw
/dev/sda2               255845     46354    209492  19% /host

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce865b76

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         134     1076323+  27  Unknown
/dev/sda2             192       32807   261985203+   7  HPFS/NTFS
/dev/sda3           36643       38913    18241807+  17  Hidden HPFS/NTFS

Grateful for the help!

---

### Post by CharlesA on 2010-07-24
> **techrunner said:**
> I did do a dual boot install from windows and retained disk format.
 
If I can't increase the size is it possible to do a backup, reinstall in a new partition, and then restore? I have done a lot of setup over the past several weeks and would prefer not to have to redo it all.

```
Filesystem           1M-blocks      Used Available Use% Mounted on
[B]/dev/loop0               16481      8232      7412  53% /
[/B]none                      1897         1      1897   1% /dev
none                      1902         1      1901   1% /dev/shm
none                      1902         1      1902   1% /var/run
none                      1902         0      1902   0% /var/lock
none                      1902         0      1902   0% /lib/init/rw
/dev/sda2               255845     46354    209492  19% /host
```

Is Ubuntu listed in Add/Remove programs? It sounds like you did a Wubi install judging from the way the file system is mounted.

This is what it looks like on my machine:

```
charles@thor:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
**/dev/sda1               288246     16486    257119   7% /**
none                      2987         1      2987   1% /dev
none                      2991         0      2991   0% /dev/shm
none                      2991         1      2991   1% /var/run
none                      2991         1      2991   1% /var/lock
none                      2991         0      2991   0% /lib/init/rw
/dev/sdb1              3755422   1726322   2029100  46% /array

```

I don't think there is a way to increase the size of the partition that was created during the Wubi install.

You'd probably have an easier time running a full install of Ubuntu in a Virtual machine (such as virtualbox or vmware) and allocating however much space as you would need to it.

---

### Post by bcbc on 2010-07-24
> **techrunner said:**
> I did do a dual boot install from windows and retained disk format.
 
If I can't increase the size is it possible to do a backup, reinstall in a new partition, and then restore? I have done a lot of setup over the past several weeks and would prefer not to have to redo it all.

Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/loop0               16481      8232      7412  53% /
none                      1897         1      1897   1% /dev
none                      1902         1      1901   1% /dev/shm
none                      1902         1      1902   1% /var/run
none                      1902         0      1902   0% /var/lock
none                      1902         0      1902   0% /lib/init/rw
/dev/sda2               255845     46354    209492  19% /host

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce865b76

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         134     1076323+  27  Unknown
/dev/sda2             192       32807   261985203+   7  HPFS/NTFS
/dev/sda3           36643       38913    18241807+  17  Hidden HPFS/NTFS

Grateful for the help!
You can migrate a wubi install to partition [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
but this requires that you create the new partition before uninstalling wubi. 

Otherwise you can save your /home directory, your installed packages, and reinstall fresh, if you prefer.

There are other options as well - LVPM doesn't work any more but on the forum howto there are some alternate instructions to migrate a wubi. I haven't tried these myself.

---

### Post by techrunner on 2010-07-24
Thanks for all the information and help.

At this point I think I'll do a backup, reformat the drive and do a real Ubuntu install, restore my apps and home directory. I actually like Ubuntu so much I have not used Windows since I installed it.

---

### Post by CharlesA on 2010-07-24
Best of luck with the reinstall. :-)

---

