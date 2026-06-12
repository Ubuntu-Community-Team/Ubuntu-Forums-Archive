---
title: "Reading fstab - new install of Maverick"
date: 2011-01-03
forum: General Help
---

### Post by Danial on 2011-01-03
Hi,

Thanks for your time to look in this question.

I just installed 10.10 on my laptop. I had 9.10 earlier but I choose to do a clean install.  Also, I tried to create a separate partition for home (/home).  Following is the output from fstab, and I am confused, specially with errors on /dev/sda5 - since that is supposed to be the root. Now I am not sure, if I did something wrong or do I need to do some fixing to the fstab.  Please advise if you have few minutes to spare.  Thanks in advance for your help. 
Danial

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=60608ee1-5c47-4c08-a6dc-e279e887b844 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=fd2d8e9f-2f74-46db-b310-7bc9b54b954b none            swap    sw              0       0

---

### Post by dandnsmith on 2011-01-03
If its just the entry in fstab you're worried about, I shouldn't.
I think it's just a way of safeguarding the partition if it detects errors on the bootup check so that no corruption while be incurred by attempting to write. Had you really got errors, then you'd be prompted to take corrective action (run fsck etc)

HTH

---

### Post by Danial on 2011-01-03
Thanks for your response.  It really ease my mind.  One more last question (I should have asked in my earlier post), so now I do have my home on s separated partition and not within the / partition (just want to be sure).

I sure appreciate your guidance, Thanks,

Danial

---

### Post by ajgreeny on 2011-01-03
Yes, you do seem to have a separate /home.

Run ```
sudo fdisk -l && df -h
``` in terminal and show us the output here.

---

### Post by Bucky Ball on 2011-01-03
Or just look in System->Administration->Gparted Partition editor.

That should show all your partitions and by the looks of it /home is on a separate partition.

---

### Post by Danial on 2011-01-03
aj,
Thanks for looking into it.

here is the output:

danial@laptop-dv9000:~$ sudo fdisk -l && df -h
[sudo] password for danial: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45325263

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18672   149977856    7  HPFS/NTFS
/dev/sda3           18672       28879    81989633    5  Extended
/dev/sda4           28880       30401    12225465    7  HPFS/NTFS
/dev/sda5           22497       28879    51270640+  83  Linux
/dev/sda6           18672       19131     3686400   82  Linux swap / Solaris
/dev/sda7           19131       22497    27031552   83  Linux

Partition table entries are not in disk order
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              49G  4.0G   42G   9% /
none                  1.5G  284K  1.5G   1% /dev
none                  1.5G  204K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda7              26G  263M   24G   2% /home
/home/danial/.Private
                       26G  263M   24G   2% /home/danial

---

### Post by Swagman on 2011-01-03
That's interesting. I just ran that command myself and saw something of a query !!

[edit-tags]

```

paul@pauls-desktop:~$ sudo fdisk -l && df -h
[sudo] password for paul: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8d83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
**Partition 1 does not end on cylinder boundary.** <--*** What's that all about ?***
/dev/sda2              13        3825    30617600    7  HPFS/NTFS
/dev/sda3            3825      121602   946039809    5  Extended
/dev/sda5            3825        4068     1951744   83  Linux
/dev/sda6            4068       16226    97654784   83  Linux
/dev/sda7           16226       17442     9764864   82  Linux swap / Solaris
/dev/sda8           17442      121602   836665344   83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
16 heads, 63 sectors/track, 395136 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27c1bb2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      395136   199148512+  42  SFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
16 heads, 63 sectors/track, 395136 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27c37f3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      395136   199148512+  42  SFS
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              92G  5.8G   82G   7% /
none                  1.6G  280K  1.6G   1% /dev
none                  1.6G  4.6M  1.6G   1% /dev/shm
none                  1.6G  396K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
/dev/sda5             1.9G  106M  1.7G   6% /boot
/dev/sda8             786G   55G  691G   8% /home
paul@pauls-desktop:~$

```

---

### Post by Bucky Ball on 2011-01-03
> **Swagman said:**
> Not putting in code tags so I can highlight it.

You can highlight things within code tags, like this:

```
 This is how you **BOLD** something in code tags, *just* the same as _anything_ else. 
```

;)

---

### Post by Swagman on 2011-01-03
> **Bucky Ball said:**
> You can highlight things within code tags, like this:

```
 This is how you **BOLD** something in code tags, *just* the same as _anything_ else. 
```

;)

Bah... Thaere's always one !!

;-)

(My bad)

---

### Post by ajgreeny on 2011-01-03
To OP:-

Yes, you have a separate /home shown here
/dev/sda7              26G  263M   24G   2% /home
at the last but one line of the output.

To swagman:-

You can safely ignore the 
**Partition 1 does not end on cylinder boundary.**
It is a relic of days before modern OSs and is of no consequence any more

---

### Post by Swagman on 2011-01-03
> **ajgreeny said:**
> To OP:-

Yes, you have a separate /home shown here
/dev/sda7              26G  263M   24G   2% /home
at the last but one line of the output.

To swagman:-

You can safely ignore the 
**Partition 1 does not end on cylinder boundary.**
It is a relic of days before modern OSs and is of no consequence any more


Thanks. Cary on as normal !!

---

### Post by Danial on 2011-01-03
> To OP:-

Yes, you have a separate /home shown here
/dev/sda7 26G 263M 24G 2% /home
at the last but one line of the output.

To swagman:-

You can safely ignore the 
Partition 1 does not end on cylinder boundary.
It is a relic of days before modern OSs and is of no consequence any more

AJ, As always, you are there to rescue poor souls on this forum.  Thanks a lot for your time and guidance. 
Danial

---

