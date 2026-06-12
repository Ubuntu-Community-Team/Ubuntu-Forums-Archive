---
title: "Ubuntu 10.04 (Lucid Lynx) - disk out of order"
date: 2011-03-04
forum: General Help
---

### Post by tinkerbox on 2011-03-04
Hi,

I googled and search on the forum and I dont seem to find people posting about this before...If there are, please point me to it..

I setup many ubuntu server before, restore the operating system using clonezilla. No fresh installed, the system configured and installed with what I needed, to do fresh install each time is too cumbersome, so I choose clonezilla to do the work. This problem never occur to me before. At least with Intel motherboard, I have this problem on my first AMD motherboard I setup: Gigabyte GA-MA770-DS3

The system I setup use 5 hard disks.The correct order if I did this command is:
```

root@tinkersoft2:~# ls -l /dev/sd*
[COLOR="Green"]brw-rw---- 1 root disk 8,  0 2011-03-03 22:21 /dev/sda
brw-rw---- 1 root disk 8,  1 2011-03-03 22:21 /dev/sda1
brw-rw---- 1 root disk 8,  2 2011-03-03 22:21 /dev/sda2
brw-rw---- 1 root disk 8,  5 2011-03-03 22:21 /dev/sda5
brw-rw---- 1 root disk 8,  6 2011-03-03 22:21 /dev/sda6[/COLOR]
brw-rw---- 1 root disk 8, 16 2011-03-03 22:21 /dev/sdb
brw-rw---- 1 root disk 8, 17 2011-03-03 22:21 /dev/sdb1
brw-rw---- 1 root disk 8, 18 2011-03-03 22:21 /dev/sdb2
brw-rw---- 1 root disk 8, 32 2011-03-03 22:21 /dev/sdc
brw-rw---- 1 root disk 8, 33 2011-03-03 22:21 /dev/sdc1
brw-rw---- 1 root disk 8, 34 2011-03-03 22:21 /dev/sdc2
brw-rw---- 1 root disk 8, 48 2011-03-03 22:21 /dev/sdd
brw-rw---- 1 root disk 8, 49 2011-03-03 22:21 /dev/sdd1
brw-rw---- 1 root disk 8, 64 2011-03-03 22:21 /dev/sde
brw-rw---- 1 root disk 8, 65 2011-03-03 22:21 /dev/sde1

```

/dev/sda - Ubuntu installed on this drive
/dev/sdb1 & /dev/sdc1 - raid 0 (md0)
/dev/sdb2 & /dev/sdc2 - raid 0 (md1)
/dev/sdd1 & /dev/sde1 - raid 0 (md2)

But with this mobo: Gigabyte GA-MA770-DS3
```

root@tinkersoft2:~# ls -l /dev/sd*
brw-rw---- 1 root disk 8, 16 2011-03-03 22:21 /dev/sda
brw-rw---- 1 root disk 8, 17 2011-03-03 22:21 /dev/sda1
brw-rw---- 1 root disk 8, 18 2011-03-03 22:21 /dev/sda2
[COLOR="Red"]brw-rw---- 1 root disk 8,  0 2011-03-03 22:21 /dev/sdb
brw-rw---- 1 root disk 8,  1 2011-03-03 22:21 /dev/sdb1
brw-rw---- 1 root disk 8,  2 2011-03-03 22:21 /dev/sdb2
brw-rw---- 1 root disk 8,  5 2011-03-03 22:21 /dev/sdb5
brw-rw---- 1 root disk 8,  6 2011-03-03 22:21 /dev/sdb6[/COLOR]
brw-rw---- 1 root disk 8, 32 2011-03-03 22:21 /dev/sdc
brw-rw---- 1 root disk 8, 33 2011-03-03 22:21 /dev/sdc1
brw-rw---- 1 root disk 8, 34 2011-03-03 22:21 /dev/sdc2
brw-rw---- 1 root disk 8, 48 2011-03-03 22:21 /dev/sdd
brw-rw---- 1 root disk 8, 49 2011-03-03 22:21 /dev/sdd1
brw-rw---- 1 root disk 8, 64 2011-03-03 22:21 /dev/sde
brw-rw---- 1 root disk 8, 65 2011-03-03 22:21 /dev/sde1

```
This cause my application failed to load, and the array went missing...
**This drive order problem happened randomly on each reboot. I need to reboot couple times to get this right**

Is there a way where I can fixed the OS drive to /dev/sda???

---

### Post by Krytarik on 2011-03-05
I don't know how to fix the actual order, but you could use their UUIDs instead of the total device paths:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by tinkerbox on 2011-03-05
> **Krytarik said:**
> I don't know how to fix the actual order, but you could use their UUIDs instead of the total device paths:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

Thanks, this help me out =)

As I mention before, I used clonezilla to install (restore using image) my system. When the system is on different disks, this make the fstab mount using UUID broken. Instead fixing this (entering new UUID for new hardisk) I choose easy way (this is my mistake) enter command such as: /sbin/swapon /dev/sda5 to restore the swap partition using new hardisk, and mount commands to mount disk that im using. 

Just now I restore the fstab using UUID. I use blkid to find UUID for the drives. After doing reboot/shutdown for my satisfaction, the drives back in order =)

Thanks Krytarik

---

