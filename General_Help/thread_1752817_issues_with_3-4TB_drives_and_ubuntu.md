---
title: "issues with 3-4TB drives and ubuntu?"
date: 2011-05-08
forum: General Help
---

### Post by JohnnyC35 on 2011-05-08
Hey, I am looking at getting a couple 3Tb Hitatchi drives. I have 10.04 installed and my motherboard is a ion-itx F-E board. Other than Windows people having issues with them I haven't found many issues but I wanted to double check here. Also do I need to have the pcie board or ...?

Thanks :)

---

### Post by srs5694 on 2011-05-08
If the drive uses 512-byte logical sector size (as, AFAIK, all internal drives still do), you'll need to use the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) to define your partitions. This has implications for the kernel, the boot loader, and the partitioning tools you use, as described [in this article I wrote.](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) Fortunately, recent versions of Ubuntu are pretty well "good to go" from the start, so you shouldn't have many issues. The biggest "gotcha" seems to be with the BIOS Boot Partition, which is a small (as small as 32 KiB, although 1 MiB is a better default size today) partition that holds part of GRUB on GPT-based disks when the computer boots using a BIOS. IIRC, the Ubuntu installer won't set this up automatically, but I might be remembering incorrectly. (If you boot with EFI, you'll need an EFI System Partition instead.)

---

