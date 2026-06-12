---
title: "Re-size disc"
date: 2011-03-20
forum: General Help
---

### Post by waterwalker23 on 2011-03-20
I have Ubuntu 10.10 installed alongside my Windows 7.  I initially was unsure of how much disc space to allocate for Ubuntu.  I would like to adjust it if possible without blowing away my Ubuntu partition.  kde partition manager installed but not clear on the disc names and how to use it.  Any help would be greatly appreciated.

Scott

---

### Post by lithopsian on 2011-03-20
I don't know how to use KDS Partition Manager, but this should be easy to do with gparted.

You won't be able to resize a disc (you get what you paid for!) but you will be able to resize, and also add or delete, partitions on that disk.

---

### Post by waterwalker23 on 2011-03-20
Resize the partition is what I meant.  I'm just not familiar with the naming convention in ubuntu.  The partition that I think is my ubuntu doesn't give me the option to resize in gparted ...

/dev/sda1          fat16
/dev/sda2          ntfs
/dev/sda4          extended
/dev/sda5          ext4
/dev/sda6          linux-swap
/dev/sda3          ntfs
unallocated      unallocated

Thanks for any assistance!!

---

### Post by Hedgehog1 on 2011-03-20
> **waterwalker23 said:**
> 
/dev/sda1          fat16
/dev/sda2          ntfs
/dev/sda4          extended
__/dev/sda5          ext4
__/dev/sda6          linux-swap
/dev/sda3          ntfs
unallocated      unallocated

There are three things you need to know:

1) You must boot from an Ubuntu LiveCD/LiveUSB to move the Linux partitions around. This makes the partitions on the disk 'unmounted'.
2) Using gparted from the LiveCD/LiveUSB, right click on the swap partition and select 'swapoff' if it is there.  This release the swap partition.
3) You have to resize the /dev/sda4 extended partition first, then you can extend the logical partition inside it.

OK - A 4th thing:  If possible, move/modify NTFS partitions using windows 7 disk manager.  If you have to resize/move an NTFS partition with gparted, please do a defrag on the partition from Windows first.

Hope this helps...

The Hedge

:KS

p.s. Primary Partitions are always number from sdx**1**-sdx**4**.  Logical partitions are always numbered starting the sdx**5** and above.

---

