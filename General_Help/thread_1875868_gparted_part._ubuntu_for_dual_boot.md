---
title: "gparted part. ubuntu for dual boot"
date: 2011-11-05
forum: General Help
---

### Post by koxx.dta on 2011-11-05
trying to partition so i can add a second OS under ubuntu....gparted tells me


A new partition table cannot be created when there are active partitions.  Active partitions are those that are in use, such as a mounted file system, or enabled swap space.
Use Partition menu options, such as unmount or swapoff, to deactivate all partitions on this device before creating a new partition table.


any help or advice greatly appreciated. i have done it before and had bt5 and ubuntu, now things are a lil dif...i have not set any partitions since 11.10 update

---

### Post by haqking on 2011-11-05
> **koxx.dta said:**
> trying to partition so i can add a second OS under ubuntu....gparted tells me


A new partition table cannot be created when there are active partitions.  Active partitions are those that are in use, such as a mounted file system, or enabled swap space.
Use Partition menu options, such as unmount or swapoff, to deactivate all partitions on this device before creating a new partition table.


any help or advice greatly appreciated. i have done it before and had bt5 and ubuntu, now things are a lil dif...i have not set any partitions since 11.10 update

boot to a gparted live CD or similar, or unmount what you wish to manipulate, if it is what you are currently suing then you cant unmount it

it cannot manipulate mounted or active disks/partitions

---

