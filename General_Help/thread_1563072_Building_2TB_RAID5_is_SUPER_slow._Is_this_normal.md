---
title: "Building 2TB RAID5 is SUPER slow. Is this normal?"
date: 2010-08-28
forum: General Help
---

### Post by flan_suse on 2010-08-28
I am building a new RAID5 array with three newly purchased hard disks. The build process is crawling at 4 MB/s and is expected to take 2.7 days (yes DAYS) to complete. Is this normal? Will this mean that the RAID5 array is going to be very slow during normal usage once I start using it?

Here is some information:

System:
* 2 GB DDR2 800MHz
* AMD Athlon X2, dual-core, 2.2 GHz

Devices:
* 1TB, 7200-RPM hard drive
* 1TB, 7200-RPM hard drive
* 1TB, 7200-RPM hard drive

LUKS encrypted partitions (-c aes-xts-plain, -s 512):
* /dev/sdb1
* /dev/sdc1
* /dev/sdd1

RAID5 array:
* 512k chunk
* 2 TB total
* /dev/mapper/sdb1_crypt
* /dev/mapper/sdc1_crypt
* /dev/mapper/sdd1_crypt

At first glance, you would think it might be kcryptd slowing down everything, but when I dd'd all three encrypted partitions, they all finished at the same time, with an average speed of 45 MB/s:
```

dd bs=8M if=/dev/zero of=/dev/mapper/sdb1_crypt &&
dd bs=8M if=/dev/zero of=/dev/mapper/sdc1_crypt &&
dd bs=8M if=/dev/zero of=/dev/mapper/sdd1_crypt

```As this build process is running, there are three instances of kcryptd consuming 5% of the CPU, each. Whereas the mdraid5 process is using 75% of the CPU.

I plan to create a secure file system based on this concept:
**3 LUKS partitions --> built into a RAID5 array (/dev/md0) ---> LVM / ext4 on top.**

I had read this will yield the best performance, since each LUKS partition will have its own kcryptd process, and right now kcryptd is not SMP-aware; so only one CPU core will will be used for each LUKS partition.

If I go the following route, then only one instance of kcryptd will be used for the entire RAID5  array (/dev/mapper/crypt_md0) and it won't utilize all cores.
**3 partitions built into RAID5 ---> /dev/md0 encrypted with LUKS ---> LVM / ext4 using /dev/mapper/crypt_md0**

Any advice on this? Am I going about it all wrong? Are these speeds normal? I'm still learning, and any criticism is welcome.

It's just that when dealing with large disks for a home PC, "starting all over" can take a VERY long time, and give the disks a major and stressful workout.

---

