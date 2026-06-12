---
title: "Partition help"
date: 2010-11-30
forum: General Help
---

### Post by CensoredBiscuit on 2010-11-30
I recently found an error in my drive partitioning, leaving ~40 gb of memory in purgatory..

I have a /~ partition of 232 gb
and a /home partition of 200 gb

anyone know what I could use this 40 gbs for?

---

### Post by plucky on 2010-11-30
> **CensoredBiscuit said:**
> I recently found an error in my drive partitioning, leaving ~40 gb of memory in purgatory..

I have a /~ partition of 232 gb
and a /home partition of 200 gb

anyone know what I could use this 40 gbs for?

Post output from a terminal of ```
sudo fdisk -l
df -h
cat /etc/fstab
```

Or install gparted and post a picture of your partition setup.

Do you really need a /root partition of 232Gb.I would recommend 10 -15GB for the /root and the rest to /home or a separate /Storage partition that you can use for long term storage.


Good Luck

---

### Post by CensoredBiscuit on 2010-11-30
> Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087ed0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       30395   244140032   83  Linux
/dev/sde2           30395       60802   244243457    5  Extended
/dev/sde5           60037       60802     6141952   82  Linux swap / Solaris
/dev/sde6           30395       55294   200000000   83  Linux
/dev/sde7           55294       60036    38095872   83  Linux

Partition table entries are not in disk order

Heres that,
How bad is that?

CB

---

### Post by Hippytaff on 2010-11-30
What about 
```

df -h

```
 
What does that look like?

---

### Post by CensoredBiscuit on 2010-11-30
> [Filesystem            Size  Used Avail Use% Mounted on
/dev/sde1             230G   12G  206G   6% /
none                  933M  272K  933M   1% /dev
none                  942M  696K  941M   1% /dev/shm
none                  942M  372K  941M   1% /var/run
none                  942M     0  942M   0% /var/lock
/dev/sde6             188G   62G  118G  35% /home

Yup, yup.

---

### Post by Hippytaff on 2010-11-30
If your dual booting you could use the extra storage for an NTFS partition for windows and ubuntu...though you might just want to expand your /home partition!?

just a couple of suggestions :-)

---

### Post by ezsit on 2010-11-30
You are currently using 12GB in your / filesystem. I would make your / filesystem 30GB and leave the rest for /home. 10-15GB for / is far too little if you plan to do any DVD burning or install major software. 

Remember, /tmp and /var live in the / filesystem and these folders need empty space to grow, if only temporarily. Burning a dual layer DVD could potentially require 16GB of free space for your /tmp folder to grow and shrink while the disk is burning. You are already at 12GB used.

Most hard drives and file systems work best when used a half capacity or lower. I always buy new, bigger hard drives when my usage gets to 60% of my current capacity. I would make your / filesystem at least 24-30GB.

---

### Post by Hippytaff on 2010-11-30
Just out of interest, why are your partitions called sde rather than sda?

---

### Post by CensoredBiscuit on 2010-12-01
> **ezsit said:**
> You are currently using 12GB in your / filesystem. I would make your / filesystem 30GB and leave the rest for /home. 10-15GB for / is far too little if you plan to do any DVD burning or install major software. 

Remember, /tmp and /var live in the / filesystem and these folders need empty space to grow, if only temporarily. Burning a dual layer DVD could potentially require 16GB of free space for your /tmp folder to grow and shrink while the disk is burning. You are already at 12GB used.

Most hard drives and file systems work best when used a half capacity or lower. I always buy new, bigger hard drives when my usage gets to 60% of my current capacity. I would make your / filesystem at least 24-30GB.

I have a 500 gb hdd?

and bah, I don't dual boot all linux baby..

---

### Post by plucky on 2010-12-01
> I have a 500 gb hdd?

and bah, I don't dual boot all linux baby.. 

That doesn't explain why it is /dev/sde when it should be /dev/sda.

---

