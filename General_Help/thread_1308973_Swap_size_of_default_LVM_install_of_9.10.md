---
title: "Swap size of default LVM install of 9.10?"
date: 2009-11-01
forum: General Help
---

### Post by hansoffate on 2009-11-01
I just installed 9.10 server on my HTPC and have done a good amount of configuration (setup mythtv, boxee, codecs, nfs share, webserver, etc).  I have noticed a few times while watching HDTV through mythtv, the frontend would lock up and freeze my whole X env.  I have to do a CTRL+ALT+BACKSPACE to regain control of my system.  This has happened about 4 times so far, and it just happened again in Boxee.

  I'm thinking it's because my swap isn't big enough.  I was wondering what the default size of the swap is for 9.10.  My previous 9.04 install I custom partitioned with 3 gigs of swap and I never ran into this problem.

Thanks for the help,
-Hans

---

### Post by JBAlaska on 2009-11-01
Good question, the wiki only says this: 
"The default partitioning recipe in the installer will in some cases allocate a swap partition that is smaller than the physical memory in the system. This will prevent the use of hibernation (suspend-to-disk) because the system image will not fit in the swap partition. If you intend to use hibernation with your system, you should ensure that the swap partition's size is at least as large as the system's physical RAM."

So maybe it's based on free disk size and not RAM....Not sure though..

Do a fdisk -l and see what your swap size is and go from there..Prolly double the RAM is good for a HTPC if you have =>2GB

---

### Post by hansoffate on 2009-11-01
Yea, I have 2gbs in my system and I heard 1.5-2.5 times the ram size is good for HTPCs.  

```

hansoffate@grunt:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
hansoffate@grunt:~$ fdisk -l
hansoffate@grunt:~$ fdisk -l
```


For some reason fdisk -l doesn't want to report anything back.  I usually like setting up the partitioning scheme, but since I've never used LVM and it's the default now, I figured I'd give it a shot.  Do you think I could resize my partitions in the LVM to make room for a bigger swap?

-Hans

---

### Post by JBAlaska on 2009-11-01
Sorry, ya gotta sudo it
```
sudo fdisk -l
```

But come to think of it that will tell you sectors I think, System monitor will give you a nice gui

And yes you can shrink or grow a partition in a LVM..gonna have to Google that though.

---

### Post by hansoffate on 2009-11-01
Doh. That should have been obvious.

```
hansoffate@grunt:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/mapper/grunt-swap_1                partition       6037496 53528   -1
hansoffate@grunt:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1870        142          0         60       1541
-/+ buffers/cache:        268       1744
Swap:         5895         52       5843

```

It looks like the swap size by default was 6 gigs.  This should be the good to run my system, it must be another problem.  Time to do more troubleshooting.  Thanks again.

---

