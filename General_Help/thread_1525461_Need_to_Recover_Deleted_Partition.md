---
title: "Need to Recover Deleted Partition"
date: 2010-07-06
forum: General Help
---

### Post by chris_1122 on 2010-07-06
On an Acer laptop, it came with Windows Vista, I reduced the partition size and installed Ubuntu with dual-boot.  It has been working fine, and recently my son even performed the upgrade to the latest Ubuntu.

The laptop came with a 2nd "recovery" partition, which my son accidentally booted to, and it removed the Ubuntu partition.  Naturally, he did not have a current backup.

I found instructions on using parted rescue to recover a deleted partition, but I cannot get any information on the partition for START and END.  The only way I can even see the drive is by booting to a live-CD (9.04) and using the Partition Editor, which shows:

[FONT=Courier New]Partition     File System   Label       Size       Used       Unused
/dev/sda1     ntfs          PQSERVICE   10.00 GB    8.13 GB    1.88 GB
/dev/sda2     ntfs          ACER        78.13 GB   32.20 GB   45.92 GB
unallocated                              2.13 GB
/dev/sda3     extended                  60.92 GB
  unallocated                           59.96 GB
  /dev/sda5   linux-swap               980.44 MB[/FONT]

reformatted since the above does not want to lay out properly:
Partition:  /dev/sda1  (ntfs)  10.00 GB  (8.13 used/1.88 unused) - this is the Acer Recovery partition
Partition:  /dev/sda2  (ntfs)  78.13 GB  (32.00 used/45.92 unused) - this is the Windows Vista partition
unallocated space:  2.13 GB
Partition:  /dev/sda3  (extended)  60.92 GB
---- unallocated space - 59.96 GB - this is the Ubuntu partition that was deleted
---- /dev/sda5  (linux-swap)  980.44 MB - this is the swap partition I set up when I first installed Linux

Any help would be greatly appreciated.  There is (unfortunately) a great deal of school and other stuff on it that we need.

---

### Post by chris_1122 on 2010-07-06
(this is not a reply)

---

### Post by chris_1122 on 2010-07-06
(this is not a reply)

---

