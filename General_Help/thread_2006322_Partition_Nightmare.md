---
title: "Partition Nightmare"
date: 2012-06-19
forum: General Help
---

### Post by th1bill on 2012-06-19
I reseived my T-60 Thinkpad with WinXP PRO and left it there as SDA1 with 12 gig and installed Ubuntu Precise on the rest. I have deleted that partition leaving SDA2, SDA5 and SDA6. SDA5 is found inside of SDA2 (reason, I can't figure) and SDA2 is listed in gparted as extended and SDA5 as my ext4 partition.

    My situation is that I wish to expand my ext4 partition to use the now empty space but I can not modify SDA2 nor 5. Any help how to do this without a reinstall will be greatly appreciated.

---

### Post by prshah on 2012-06-19
> **th1bill said:**
> SDA1 with 12 gig... I have deleted that partition leaving SDA2, SDA5 and SDA6.
...wish to expand my ext4 partition to use the now empty space 

Here's a quick and dirty partitioning primer: You can have a maximum of 4 partitions. ONE of these can be an extended partition (the others are called primary partitions). An extended partition can then have upto 128 (?) "logical" partitions.

In your current situation, you have deleted the primary partition (sda1) which exists outside of the extended partition (sda2). Therefore, the free space is outside of sda2.

You need to resize/move sda2 to include the free space. You can then resize/move your other partitions to include the free space.

However, all partitions need to be UNMOUNTED to allow resizing / moving. To do this, you need to boot off a live CD/USB, and run gparted. If any partitions are displaying a "key"-type symbol, right click it, and choose "unmount" / "swapoff".

You will now be allowed to resize / move the partitions.

I have never had a failed gparted move/resize; however your mileage may vary. So please ensure you have a backup of important files.

Please post back if you need more details.

---

### Post by th1bill on 2012-06-19
> **prshah said:**
> Here's a quick and dirty partitioning primer: You can have a maximum of 4 partitions. ONE of these can be an extended partition (the others are called primary partitions). An extended partition can then have upto 128 (?) "logical" partitions.

In your current situation, you have deleted the primary partition (sda1) which exists outside of the extended partition (sda2). Therefore, the free space is outside of sda2.

You need to resize/move sda2 to include the free space. You can then resize/move your other partitions to include the free space.

However, all partitions need to be UNMOUNTED to allow resizing / moving. To do this, you need to boot off a live CD/USB, and run gparted. If any partitions are displaying a "key"-type symbol, right click it, and choose "unmount" / "swapoff".

You will now be allowed to resize / move the partitions.

I have never had a failed gparted move/resize; however your mileage may vary. So please ensure you have a backup of important files.

Please post back if you need more details.

At 67 I must getting to be senile!  I thought I had taken these steps you've outlined but I rebooted my gparted cd and guess what, it works like it should!

Thank you for the gumpsion to tread on an old nerd's toes.

---

