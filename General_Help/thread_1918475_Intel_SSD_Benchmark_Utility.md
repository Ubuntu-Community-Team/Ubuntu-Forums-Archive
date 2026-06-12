---
title: "Intel SSD Benchmark Utility"
date: 2012-02-01
forum: General Help
---

### Post by Welly Wu on 2012-02-01
Hi. I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 1,066 MHz SDRAM and an Intel 2nd Generation 2.5" 34nm MLC NAND FLASH X25-M 160 gigabyte Solid State Drive. When I was running Microsoft Windows 7 Ultimate 64 bit, there was a software application that I used to test my Intel SSD benchmark results called AS SSD. Is there any way that I can benchmark the results for my Intel SSD in Ubuntu 11.10 64 bit? What software application do I need to download, install, and use to do this? Thank you.

---

### Post by dcstar on 2012-02-01
> **Welly Wu said:**
> Hi. I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 1,066 MHz SDRAM and an Intel 2nd Generation 2.5" 34nm MLC NAND FLASH X25-M 160 gigabyte Solid State Drive. When I was running Microsoft Windows 7 Ultimate 64 bit, there was a software application that I used to test my Intel SSD benchmark results called AS SSD. Is there any way that I can benchmark the results for my Intel SSD in Ubuntu 11.10 64 bit? What software application do I need to download, install, and use to do this? Thank you.

All Disk benchmarks are done by the Disk Utility.

---

### Post by Welly Wu on 2012-02-04
When I run Disk Utility, I can only do a read benchmark. When I try to select and run the read and write benchmark, I am getting this error:

The disk seems to have usage `raid' - write benchmarking requires the disk to be completely empty.

How do I fix this problem so that I can run a read and write benchmark on my Intel X25-M 160 gigabyte SSD?

---

### Post by dcstar on 2012-02-04
> **Welly Wu said:**
> When I run Disk Utility, I can only do a read benchmark. When I try to select and run the read and write benchmark, I am getting this error:

The disk seems to have usage `raid' - write benchmarking requires the disk to be completely empty.

How do I fix this problem so that I can run a read and write benchmark on my Intel X25-M 160 gigabyte SSD?

You wipe the partitions from it, as is required with the Write benchmark.

---

