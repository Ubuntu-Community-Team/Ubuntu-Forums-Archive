---
title: "RAID 0 (from 4 partitions) is only 2 times faster than one hard drive"
date: 2012-02-21
forum: General Help
---

### Post by masuch on 2012-02-21
Hi,

I created RAID 0 from 4 partitions where each partition is located on different SATA II hard drive.

When I measured speed by:
sudo hdparm -tT /dev/sda
sudo hdparm -tT /dev/sdb
sudo hdparm -tT /dev/sdc
sudo hdparm -tT /dev/sdd

it is always aproximately like following:
 Timing cached reads:   35184 MB in  2.00 seconds = 17613.44 MB/sec
 Timing buffered disk reads: 404 MB in  3.01 seconds = 134.06 MB/sec

but for RAID 0 I have got:
sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   33210 MB in  2.00 seconds = 16623.39 MB/sec
 Timing buffered disk reads: 786 MB in  3.00 seconds = 261.94 MB/sec


which is only 2 times faster ... .

-----------------
dd if=/dev/zero of=~/test.img bs=8k count=256k
262144+0 records in
262144+0 records out
2147483648 bytes (2.1 GB) copied, 21.0776 s, 102 MB/s

dd if=/dev/zero of=/mnt/md0/test.img bs=8k count=256k
262144+0 records in
262144+0 records out
2147483648 bytes (2.1 GB) copied, 7.61225 s, 282 MB/s
------------

According to wikipedia "http://en.wikipedia.org/wiki/RAID" I should get 4 times faster read/write.

Why is it only 2 times faster instead of 4 times faster ?

Where could be the problem ?
Would it be faster if I gonna create 4 partitions for RAID 0 on the same hard drive (I don't think so, but  maybe I am wrong.) ?

Thank you for any clue to linux newbee.
Regards,
Martin

---

### Post by dcstar on 2012-02-22
> **masuch said:**
> Hi,

I created RAID 0 from 4 partitions where each partition is located on different SATA II hard drive.
........
Thank you for any clue to linux newbee.
Regards,
Martin

And you are aware that if **one** of your hard drives fails, you lose **all** of your data?

Statistically now you are **4 times** as likely to lose data due to drive failure than with just one drive.

---

### Post by masuch on 2012-02-22
> **dcstar said:**
> And you are aware that if **one** of your hard drives fails, you lose **all** of your data?

Statistically now you are **4 times** as likely to lose data due to drive failure than with just one drive.

I am definitely aware of loosing of data. I did my homework. Would it be possible to stay on topic ?

---

### Post by masuch on 2012-02-22
Couple of "RAID 0" optimalizations what I did according to:

[http://www.overclockers.com/forums/showthread.php?t=689275](http://www.overclockers.com/forums/showthread.php?t=689275)
and
[http://erikugel.wordpress.com/2011/04/14/the-quest-for-the-fastest-linux-filesystem/](http://erikugel.wordpress.com/2011/04/14/the-quest-for-the-fastest-linux-filesystem/)

mdadm --create /dev/md0 --chunk=64 --level=0 --raid-devices=4 /dev/sda2 /dev/sdb2 /dev/sdd2 /dev/sde7
mkfs.ext4 -b 4096 -E stride=16,stripe-width=64 /dev/md0
tune2fs -O has_journal -o journal_data_writeback /dev/md0
tune2fs -O dir_index /dev/md0
e2fsck -D /dev/md0

/etc/fstab:
/dev/md0  /mnt/md0 ext4 noatime,nodiratime,data=writeback,stripe=16,barrier=0,errors=remount-ro 1 1

mdadm.conf:
ARRAY /dev/md0 metadata=1.2 UUID=f5671042:3c222058:dfff829f:7016466f

mdadm compiled and installed last version 3.2.2.


--- I am as well going to change filesystem from ext4 to xfs because I have red it should be faster.

but original question stayed the same.
Why is it only 2 times faster instead of 4 times ?

---

