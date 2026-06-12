---
title: "Slow? Copy rate onto sata"
date: 2012-10-01
forum: General Help
---

### Post by starwars2020 on 2012-10-01
Hi all, In trying to copy ~100GB of NTFS data in small and large files from an ext USB disk to the SATAII hard disk, the rate is only ~15MB/sec. Is this normal? Thank you.

Running 64bit Pangolin 
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 002: ID 13fd:1340 Initio Corporation Hi-Speed USB to SATA Bridge

---

### Post by rubylaser on 2012-10-01
That's a little slow for USB2 (maxes out around 35 MB/s), but within the normal range for a file transfer.  If it's a USB3 external disk, then you transfer speeds are much slower than they should be.

---

### Post by starwars2020 on 2012-10-02
> **rubylaser said:**
> That's a little slow for USB2 (maxes out around 35 MB/s), but within the normal range for a file transfer.  If it's a USB3 external disk, then you transfer speeds are much slower than they should be.


It's a USB2 external Hard Disk, I just thought its USB2 read speed should be more, as it only reads from it. It writes onto the SATAII..

---

### Post by Grenage on 2012-10-02
> **starwars2020 said:**
> It's a USB2 external Hard Disk, I just thought its USB2 read speed should be more, as it only reads from it. It writes onto the SATAII..

That's why many of us opt for eSATA connectivity over USB, not only is it much faster, but it's also much more reliable (speed-wise) in Ubuntu.

---

### Post by starwars2020 on 2012-10-04
> **Grenage said:**
> That's why many of us opt for eSATA connectivity over USB, not only is it much faster, but it's also much more reliable (speed-wise) in Ubuntu.
It's got eSATA port, the m/b doesn't though...Anyway, recopied the data after I downgraded to Ubuntu 11.10 (which by memory was a lot faster than 12..) and the copy rate onto the SATA PC HD increased and topped ~30MB/sec..!! Don't know why..

---

