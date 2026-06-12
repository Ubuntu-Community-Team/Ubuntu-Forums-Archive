---
title: "Grub2 40_custom partition 3 entry never boots"
date: 2012-04-30
forum: General Help
---

### Post by Trapper on 2012-04-30
U12.04
XU12.04
U10.04

I have a situation where I cannot create a successful 40_custom boot entry for anything I put on the 3rd partition of my hard drive. On the other hand I can boot to that partition via a 30_os-prober entry. Uniquely, I can boot to any other partition via 40_custom entries.

Here are two schemes:

The first is  for sda8, which has a U 10.04 install and I can successfully boot into it via either the 30 or 40 menuentry. 
```

30_os-prober:

menuentry "Ubuntu, with Linux 2.6.32-41-generic (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 30347141-4482-4d29-b893-64f4dc07fd1e
    linux /boot/vmlinuz-2.6.32-41-generic root=UUID=30347141-4482-4d29-b893-64f4dc07fd1e ro
    initrd /boot/initrd.img-2.6.32-41-generic
}

40_custom:

menuentry "Ubuntu 10.04 LTS (on /dev/sdb8)"  {

    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 30347141-4482-4d29-b893-64f4dc07fd1e
    chainloader +1
}


```Now the 30 & 40 entries for sdb3. I can always boot from the 30_os-prober entry but the 40_custom entry always gets me the invalid signature message.
```

30_os-prober:

menuentry "Ubuntu, with Linux 3.2.0-24-generic (on /dev/sdb3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 576da831-a99f-41a2-8799-7ec1a25b309a
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=576da831-a99f-41a2-8799-7ec1a25b309a ro
    initrd /boot/initrd.img-3.2.0-24-generic
}

40_custom:

menuentry "Xubuntu 12.04 LTS  (on /dev/sdb3)"  {

    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 576da831-a99f-41a2-8799-7ec1a25b309a
    chainloader +1

}

```I've even tried total simplicity with the the failing 40 custom entry, such as:

set root=(hd0,3)
chainloader +1

That fails, as does absolutely any set root= combination I can think of, including hd1 attempts.

Here's my fdisk info for this drive:

```
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    61432559    30716248+   7  HPFS/NTFS/exFAT
/dev/sdb2        61432560   161790614    50179027+   7  HPFS/NTFS/exFAT
/dev/sdb3       161790615   233890334    36049860   83  Linux
/dev/sdb4       233890396   488392064   127250834+   5  Extended
/dev/sdb5       233890398   379294649    72702126   83  Linux
/dev/sdb6       379294713   388098269     4401778+  82  Linux swap / Solaris
/dev/sdb7       388098333   437273234    24587451   83  Linux
/dev/sdb8       437273298   488392064    25559383+  83  Linux
```As far as I am concerned this fdisk info is inaccurate as is grub's. I say that because I only have one (1) hard drive on this box. Why is my hard drive sdb??? Secondly, there's a U12.04 install on sdb2 and that's the install that maintains the MBR. Why is fdisk saying it's a  HPFS/NTFS/exFAT partition?

Whatever, I can never get a custom boot entry to boot on partition 3 and I have tried U11.10, U1004 U 12.04 and XU12.04 on it. Always the same failing result. 

There's even more history. This drive used have a a totally different partition scheme and I could never get a partition 3 custom boot entry to work with that either. Custom entries are always successful with other partitions.

Anyone have any sort of idea what's wrong?

---

