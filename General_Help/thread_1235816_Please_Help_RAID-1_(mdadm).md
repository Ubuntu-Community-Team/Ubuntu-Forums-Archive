---
title: "Please Help: RAID-1 (mdadm)"
date: 2009-08-09
forum: General Help
---

### Post by ag3 on 2009-08-09
I have been stuck on this for over a week and it's driving me nuts.

I have a fresh install of Ubuntu Server 9.04 x86-64 with software raid (level 1) during installation. I have four SATA disks present (2x 750 GB (sda, sdc), 2x 1.5 TB (sdb, sdd).

I created 3 partitions on the 750 GB, md0 (sda1, sdc1) which is boot, md1 (sda2, sdc2) which is swap, and md2 (sda2, sdc2) which is root. No problems there.

Now I am trying to create a RAID array out of the 1.5 TBs (which should be md3). The problem is that once I reboot the server, md3 turns into md_d3 and reports the following in /proc/mdstat... 

```

 root@server1:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md_d3 : inactive sdb1[0](S)
      1465135936 blocks

md2 : active raid1 sda3[0] sdc3[1]
      724258304 blocks [2/2] [UU]

md1 : active raid1 sda2[0] sdc2[1]
      7815552 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdc1[1]
      497856 blocks [2/2] [UU]

unused devices: <none>


```As you can see, sdd1 is missing! I don't know why this is happening. I followed this guide thoroughly...

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

Everything is good until I reboot the server! Is there a step that I am missing? Please help!

Thank you for your time, I greatly appreciate any input.

---

### Post by ag3 on 2009-08-10
bump!

---

### Post by ag3 on 2009-08-11
Anyone!? Please.

---

### Post by ag3 on 2009-08-11
Nevermind. I figured it out myself. The problem was /etc/mdadm.conf when Ubuntu uses /etc/mdadm/mdadm.conf.

---

