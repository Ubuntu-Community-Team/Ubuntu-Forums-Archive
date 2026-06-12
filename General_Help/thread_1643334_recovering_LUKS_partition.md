---
title: "recovering LUKS partition"
date: 2010-12-11
forum: General Help
---

### Post by BinaryMn on 2010-12-11
I've been trying to resize (grow) a LUKS partition on, in my case, /dev/sda7. Help suggested in another thread on this forum resulted in cryptsetup no longer recognizing the partition as a LUKS device. In essence, I've lost everything currently.

All I did was delete the partition with fdisk, then recreate the partition with the same start cylinder with the end cylinder being a little farther down the drive because of the extra space I was adding to the partition. I haven't formatted or tried putting another filesystem over where I had the LUKS partition.

I've tried recreating the partition with fdisk using the original start and end cylinders, but the block size is different and still isn't being recognized as a LUKS device. I'm currently running testdisk for the third time hoping it'll find the missing partition.

Please help.

---

### Post by frostschutz on 2010-12-11
What does hexdump on the partition in question give you? For LUKS it should look similar to this:

```
hexdump -C -n 512 /dev/sdb13
00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |n...............|
00000040  00 00 00 00 00 00 00 00  73 68 61 32 35 36 00 00  |........sha256..|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

```

If it doesn't look like that (starting with LUKS followed by the cipher names) then the partition is not in the same start place, or the LUKS header was overwritten. Without LUKS header the chances of rescue are zero so you better find it...

You can obtain possible byte positions of the LUKS header using grep on main the disk device:

```
grep -a -b -P --only-matching 'LUKS\xba\xbe' /dev/sdb
```

However since the search string is only 6 bytes this can also yield random false matches. So take a closer look at those byte positions to see if it's actually a complete header, and then see if you can create a partition that starts exactly there, or simply set up a loop device with an offset. If you can open the LUKS container, be sure to mount filesystems in there as read only, and pull a backup first before doing anything else.

---

### Post by BinaryMn on 2010-12-11
For anyone that wants to help, here's what fdisk -l looks like before I deleted the partitions. Note that sda8 is an empty partition.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8abaa97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             285       25924   205941760    5  Extended
/dev/sda2   *       25924       30402    35971072    7  HPFS/NTFS
/dev/sda3               1         285     2284544    b  W95 FAT32
Partition 3 does not end on cylinder boundary.
/dev/sda5           19151       25923    54403072    7  HPFS/NTFS
/dev/sda6           17838       19150    10546176   83  Linux
/dev/sda7             285       17582   138939392   83  Linux
/dev/sda8           17582       17837     2048000   83  Linux
```

This is what it looks like now.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8abaa97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             285       25924   205941760    5  Extended
/dev/sda2   *       25924       30402    35971072    7  HPFS/NTFS
/dev/sda3               1         285     2284544    b  W95 FAT32
Partition 3 does not end on cylinder boundary.
/dev/sda5           19151       25923    54403072    7  HPFS/NTFS
/dev/sda6           17838       19150    10546176   83  Linux
/dev/sda7             285       17582   138941815+  83  Linux
```

---

### Post by BinaryMn on 2010-12-11
> **frostschutz said:**
> What does hexdump on the partition in question give you? For LUKS it should look similar to this:

```
hexdump -C -n 512 /dev/sdb13
00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |n...............|
00000040  00 00 00 00 00 00 00 00  73 68 61 32 35 36 00 00  |........sha256..|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

```

If it doesn't look like that (starting with LUKS followed by the cipher names) then the partition is not in the same start place, or the LUKS header was overwritten. Without LUKS header the chances of rescue are zero so you better find it...

You can obtain possible byte positions of the LUKS header using grep on main the disk device:

```
grep -a -b -P --only-matching 'LUKS\xba\xbe' /dev/sdb
```

However since the search string is only 6 bytes this can also yield random false matches. So take a closer look at those byte positions to see if it's actually a complete header, and then see if you can create a partition that starts exactly there, or simply set up a loop device with an offset. If you can open the LUKS container, be sure to mount filesystems in there as read only, and pull a backup first before doing anything else.

```
root@ubuntu:/home/ubuntu# hexdump -C /dev/sda7 | grep LUKS
000f8200  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
```

Looks like something is still there. Thanks for the help.

---

### Post by frostschutz on 2010-12-11
Hope that's not bad news, because if the LUKS header is in the correct place but you can't open it, then there's something wrong with the header later on or your passphrase is wrong.

What error message do you get?

---

### Post by BinaryMn on 2010-12-11
> **frostschutz said:**
> Hope that's not bad news, because if the LUKS header is in the correct place but you can't open it, then there's something wrong with the header later on or your passphrase is wrong.

What error message do you get?

My header isn't in the first 512 bytes of the partition. Look at the hex address. The header is there, but in the wrong location. Maybe it's because cylinder 285 is also where an extended partition starts. However, to answer your question.

```
root@ubuntu:/home/ubuntu# sudo cryptsetup --verbose luksOpen /dev/sda7 sda7_crypt
Command failed with code 22: /dev/sda7 is not a LUKS device
```

---

### Post by BinaryMn on 2010-12-11
Making progress.

```
root@ubuntu:/home/ubuntu# mount -o loop,offset=0x000f8200 /dev/sda7 /media/test
mount: unknown filesystem type 'crypto_LUKS'
```

---

### Post by frostschutz on 2010-12-11
Eh, whoops, completely missed that in your hexdump output :-\"

So that's great news since it should work once you have it in the correct place.

So with a loop device it could be something like:

```

losetup -o 0xf8200 -r -f /dev/sda7
losetup -a
/dev/loop0: (/dev/sda7), offset 1016320
cryptsetup luksOpen /dev/loop0 luksrecover
mount -o ro /dev/mapper/luksrecover /mnt/recover

```

As for moving the partition to the correct place, try your luck with sfdisk (dump into a text file with byte/sector unit, edit a copy of the text file, and change the position accordingly, and try to restore that)

---

### Post by BinaryMn on 2010-12-11
I've been trying something like that already, but losetup isn't liking the offset. Instead of starting the offset at 0xf8200 or 0x000f8200, it keeps starting the offset at 000000f0. :(

Got any other ideas?

---

### Post by bodhi.zazen on 2010-12-11
> **BinaryMn said:**
> All I did was delete the partition with fdisk, then recreate the partition with the same start cylinder with the end cylinder being a little farther down the drive because of the extra space I was adding to the partition. I haven't formatted or tried putting another filesystem over where I had the LUKS partition.

First, stop do not panic, and think ;)

fdisk does not over write data, simply re-run fdisk and undo the changes you made and all should be well again.

---

### Post by BinaryMn on 2010-12-11
> **bodhi.zazen said:**
> First, stop do not panic, and think ;)

fdisk does not over write data, simply re-run fdisk and undo the changes you made and all should be well again.
I've done that. It is not working.

The start and end cylinders are the same, but the LUKS header is not in the beginning of the partition. Look at the hexdump snippets above to see what is happening. I believe this is happening because there's an extended partition on the same cylinder the logical partition that I had LUKS on.

I'm not panicking. I'm mildly irritated, but I know that the data is still there. It's just matter of creating a partition in the right spot on the hard drive where the LUKS filesystem is.

---

### Post by BinaryMn on 2010-12-11
I'm using Clonezilla and making a image of the drive (on loaned storage) as it is right now before I make any more changes.

I think this is a cylinder boundary problem. sda1 and sda7 start on cylinder 285. sda3 ends on 285 and fdisk gives me that "Partition 3 does not end on cylinder boundary" error.

I'm going to try moving sda1 and sda3 just a little bit to see if I can get it back on a cylinder boundary. Then I'll try this again and see if I have the same problem. Worst case, I'm back to where I started.

---

### Post by frostschutz on 2010-12-12
> **BinaryMn said:**
> I've been trying something like that already, but losetup isn't liking the offset. Instead of starting the offset at 0xf8200 or 0x000f8200, it keeps starting the offset at 000000f0. :(

eeeh... not liking the offset?! :-k

works for me ... although I specify in byte using the commands I gave earlier

It's not even bound to 512 byte sectors, I can move +1 byte and have L of LUKS missing.

```

# grep -a -b -P --only-matching 'LUKS\xba\xbe' /dev/sdb
1048576:LUKSº¾
# losetup -o 1048576 -r -f /dev/sdb
# hexdump -C -n 128 /dev/loop0
00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
# losetup -o 1048577 -r -f /dev/sdb
# hexdump -C -n 128 /dev/loop1
00000000  55 4b 53 ba be 00 01 61  65 73 00 00 00 00 00 00  |UKS....aes......|

```So there should not be a thing such as an offset losetup does not like ... *confused*

Have to be a bit careful with fdisk, it overwrites bytes for the logical partitions (sdax with x > 4). With sfdisk you can store (and restore) those if it fails (sfdisk -O, sfdisk -I). sfdisk also lets you dump the partition table into a file (sfdisk -d) so you can move a partitions starting point by simply editing the sector number of that partition. So sfdisk gives you everything you need (including the perfect undo function), if you know how to use it.

Good idea to make a complete image anyway though. :)

I never use plain fdisk anymore, because cfdisk and sfdisk do a much better job; (for that matter I don't use dos partitions anymore if I don't have to)

---

### Post by BinaryMn on 2010-12-12
I may use sfdisk instead. I probably would've used it from the beginning if I had known about it. Obviously, I know a thing or two about partitions and filesystems, but this is stepping a little bit out of my realm of expertise.

Could you elaborate about how fdisk overwrites bytes for logical partitions. I'm rereading that sentence over and scratching my head. Something isn't making sense.

---

### Post by BinaryMn on 2010-12-12
SUCCESS!

After fixing the cylinder boundary issue, I read a tutorial on sfdisk, sent the output of sfdisk -d to a text file, and started manually editing the sector start and size for /dev/sda7, writing the changes, then using hexdump to see where the LUKS header was until it lined up with 0x00000000.

Thanks a bunch. Definitely learned a bit more on drive partitioning.

---

### Post by frostschutz on 2010-12-12
dos has only 4 partitions... if you need more you create an extended partition, in which you can create logical partitions... and the information about logical partitions is stored "outside" so it overwrites some sectors somewhere.

More detail here
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

---

### Post by BinaryMn on 2010-12-12
I just went back and had to manually set the new size of sda7 by changing the 'size=' value so I could expand the LUKS filesystem on it. Trying to use fdisk to delete and recreate the partition like I was told to do breaks things.

---

### Post by BinaryMn on 2010-12-12
<s>And now I can't get GRUB repaired. The bootloader is there, but the computer doesn't load it when I reboot. Tried all of the different ways to repair the bootloader, even chrooting in. Even using the testdisk MBR doesn't boot.</s>

Forgot to set the /boot partition as bootable. :oops:

---

