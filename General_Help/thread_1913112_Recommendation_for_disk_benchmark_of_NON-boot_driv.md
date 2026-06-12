---
title: "Recommendation for disk benchmark of NON-boot drive?"
date: 2012-01-21
forum: General Help
---

### Post by Mugsy323 on 2012-01-21
I need a Linux disk benchmarking program that will test my SSD.

Problem is, the SSD is NOT my boot drive, and while I've found plenty of Linux disk benchmarking programs, they all only test the BOOT drive. I need one that will let me test ANY drive of my choosing.

Thx.

---

### Post by dcstar on 2012-01-22
> **Mugsy323 said:**
> I need a Linux disk benchmarking program that will test my SSD.

Problem is, the SSD is NOT my boot drive, and while I've found plenty of Linux disk benchmarking programs, they all only test the BOOT drive. I need one that will let me test ANY drive of my choosing.

Thx.

Like the built-in Disk Utility?

---

### Post by Mugsy323 on 2012-01-22
> **dcstar said:**
> Like the built-in Disk Utility?
I'm not familiar with any "built-in utility" that includes a benchmark.

---

### Post by Cheesemill on 2012-01-22
It's called Disk Utility and comes installed by default.

Just select the drive you want to test and click on 'Benchmark'.

---

### Post by Mugsy323 on 2012-01-22
> **Cheesemill said:**
> It's called Disk Utility and comes installed by default.
Thanks, but unfortunately, "Disk Unitilty" can only benchmark empty unformatted drives. Mine is currently my Win7 boot drive.

I've run benchmarks in Win7, but got terrible results that I suspect are due to lousy drivers.

I need to benchmark the drive outside of Windows.

---

### Post by Cheesemill on 2012-01-22
That's odd.

My machine only has one drive which is full with a mix of NTFS, ext4, and swap partitions and it benchmarks that OK.



Edit - Looks like I'd only tried a read only test, when trying a read/write test I get the same error as you.

---

### Post by Cheesemill on 2012-01-22
For a quick write test you could use dd to measure speed:
```
dd if=/dev/zero of=/mnt/Win7/ddfile bs=8k count=2000000
```

Make sure you replace /mnt/Win7 with the actual mount point of your drive.
This will write a 16GB file to the disk and give you an average speed (I used such a large file to negate the affect of any disk caching), just delete the file after you are done.

---

### Post by Mugsy323 on 2012-01-22
> **Cheesemill said:**
> That's odd.

My machine only has one drive which is full with a mix of NTFS, ext4, and swap partitions and it benchmarks that OK.

Edit - Looks like I'd only tried a read only test, when trying a read/write test I get the same error as you.
Yes, it is my "Write" speed that needs checking.

Benchmarks under Windows report good read speeds, but deplorable write speeds. I suspect it is the driver, but need to test under another OS to know for sure.

---

