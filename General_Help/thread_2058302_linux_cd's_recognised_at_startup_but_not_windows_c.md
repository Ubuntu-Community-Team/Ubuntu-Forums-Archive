---
title: "linux cd's recognised at startup but not windows cd's"
date: 2012-09-15
forum: General Help
---

### Post by ancylla on 2012-09-15
hi, i installed ubuntu 12.04 LTS, completely overwriting and deleting windows 7, i have a windows 7 disk that works on other pc's. if i put a disk that has a Linux distribution on, it is recognized and boots into the cd, if i load a cd with a windows OS on it just loads straight back into UBUNTU. I need to totally uninstall ubuntu and go back to windows 7.
Thank you
Ancylla

---

### Post by Bucky Ball on 2012-09-15
Have you changed the boot device in BIOS to boot from the optical drive first?

If you are intending a dual-boot I would save some time and headache by installing Windows first disk, first partition, leaving the rest free space. Make sure that's happening then boot up the Ubuntu LiveCD, create an extended partition with the free space, then install Ubuntu to logical drives inside the extended partition.

---

### Post by ancylla on 2012-09-15
> **Bucky Ball said:**
> Have you changed the boot device in BIOS to boot from the optical drive first?

yes this has been done

boot order is
1. disk drive
2.hard drive

---

### Post by ancylla on 2012-09-15
> **Bucky Ball said:**
> 

If you are intending a dual-boot I would save some time and headache by installing Windows first disk, first partition, leaving the rest free space. Make sure that's happening then boot up the Ubuntu LiveCD, create an extended partition with the free space, then install Ubuntu to logical drives inside the extended partition.

I am not intending to dual boot with windows i just want windows, thank you

---

