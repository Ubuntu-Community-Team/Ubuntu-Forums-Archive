---
title: "grub can't boot windows"
date: 2009-07-26
forum: General Help
---

### Post by mayagamer on 2009-07-26
I have a usb harddisk.
there are 3 partition in it.
first partition is linux swap
second is ubuntu
third is windows.
I want this disk could run in most pc

grub setup in MBR
can boot ubuntu,but can't boot windows
Error codes:Error 12 Invalid device requested

please help me!

menu.lst code is here:
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		3ca6b9ce-7708-4b5e-9145-69ceb9702796
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=3ca6b9ce-7708-4b5e-9145-69ceb9702796 ro locale=zh_CN quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		windows
uuid		3d6b-07d1
makeactive
chainloader	+1
```

---

### Post by Bucky Ball on 2009-07-26
```
title         Windows 95/98/NT/2000
root         ** (hd0,0)**
savedefault
makeactive
chainloader   +1

```Replace the part in bold with the appropriate details (probably something like (hd2,0) depending on number of hard drives you have).

To get the details, boot Ubuntu and check in System->Administration->Partition Editor.

sda1=(hd0,0); sda2=(hd0,1); sdb2=(hd1,1) etc

---

### Post by mayagamer on 2009-07-26
> **Bucky Ball said:**
> ```
title         Windows 95/98/NT/2000
root         ** (hd0,0)**
savedefault
makeactive
chainloader   +1

```Replace the part in bold with the appropriate details (probably something like (hd2,0) depending on number of hard drives you have).

To get the details, boot Ubuntu and check in System->Administration->Partition Editor.

sda1=(hd0,0); sda2=(hd0,1); sdb2=(hd1,1) etc

I tried many times,but it did not work.
And I want use this harddisk by plugin every PC,so I think use uuid is the better way.The ubuntu partition is using uuid, and it works correctly.

Thank you

---

### Post by Bucky Ball on 2009-07-26
> **mayagamer said:**
> I think use uuid is the better way.The ubuntu partition is using uuid, and it works correctly.



But you are chainloading the Windows bootloader and I don't think that will understand the same syntax. I could be wrong, but you are talking two different languages there.

Can't you just set your machine to boot from USB drive? Aren't you going to need to do that on other machines as there is no grub resident anywhere but the external USB drive?

---

### Post by grayn0de on 2009-07-26
What is the output of 'sudo fdisk -l' (lowercase L, for list), when you boot into Ubuntu. Also, this might be a stupid question, but did you install Windows first? If so, where you able to boot into it before installing Ubuntu?

Another thing: Is Windows your front-most partition? Meaning, is it actually sda1(hda0,0)? From your description, it sounds like the last partition is Windows, that would make it sda3(hda0,3) or whatever.

---

### Post by mayagamer on 2009-07-26
> **Bucky Ball said:**
> But you are chainloading the Windows bootloader and I don't think that will understand the same syntax. I could be wrong, but you are talking two different languages there.

Can't you just set your machine to boot from USB drive? Aren't you going to need to do that on other machines as there is no grub resident anywhere but the external USB drive?

I have 2 machines.They are all windows only.I can set machine to boot from USB drive and startup ubuntu in it.

```
MACHINE(1 partition)
              only windows in it

USB DRIVE(3 partition)
              first partition is linux swap
              second is ubuntu
              third is windows(which I want to startup)

```

---

### Post by Bucky Ball on 2009-07-26
Installing Windows first on the external drive would have made life a lot easier. You will now need to map the drive in the appropriate menu.lst as Windows demands to be first partition (primary), first drive and if it is physically not you need to trick it into thinking it is.

---

### Post by mayagamer on 2009-07-26
> **grayn0de said:**
> What is the output of 'sudo fdisk -l' (lowercase L, for list), when you boot into Ubuntu. Also, this might be a stupid question, but did you install Windows first? If so, where you able to boot into it before installing Ubuntu?

Another thing: Is Windows your front-most partition? Meaning, is it actually sda1(hda0,0)? From your description, it sounds like the last partition is Windows, that would make it sda3(hda0,3) or whatever.

output of 'sudo fdisk -l':
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf8db35e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sda2            6376       19457   105081165    f  W95 Ext'd (LBA)
/dev/sda5            6376       19457   105081133+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa244fa49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c2eed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         122      979933+  82  Linux swap / Solaris
/dev/sdc2             123        2432    18555075   83  Linux
/dev/sdc3            2433        4870    19583235    5  Extended
/dev/sdc5            2433        4870    19583203+   b  W95 FAT32

```

the last device is the very USB drive

---

### Post by grayn0de on 2009-07-26
Try:

```

title        Windows 
rootnoverify    (hd2,4)
savedefault
makeactive
chainloader    +1

```

---

### Post by Bucky Ball on 2009-07-26
> **grayn0de said:**
> Try:

```

title        Windows 
rootnoverify    (hd2,4)
savedefault
makeactive
chainloader    +1

```

I think you are still going to need to map the drive. If only it were that easy. Hopefully I am proved wrong.

```

title        Windows 
rootnoverify    (hd2,4)
[B]map (hd2,0) (hd2,4)
map (hd2,4) (hd2,0)[/B]
savedefault
makeactive
chainloader    +1

```[/quote]

... I think is the syntax, or possibly swapped:

```

title        Windows 
rootnoverify    (hd2,4)
[B]map (hd2,4) (hd2,0)
map (hd2,0) (hd2,4)[/B]
savedefault
makeactive
chainloader    +1

```It is something like that but you might want to google and double check. As I said, Windows demands the first partition so you need to fool it. This is why it is advisable (but not imperative) to install MS on the first partition. Then you don't have to stuff about with mapping it.

---

### Post by merlinus on 2009-07-26
This might work:

title        Windows 
rootnoverify    (hd2,4)
[B]map (hd0) (hd2)
map (hd2) (hd0)[/B]
savedefault
makeactive
chainloader    +1

Also, make sure hd2 is listed in /boot/grub/device.map:
(hd2)  /dev/sdc

---

### Post by grayn0de on 2009-07-26
> **Bucky Ball said:**
> Windows demands the first partition so you need to fool it.

+1 ... I forgot about that. :)

---

### Post by Bucky Ball on 2009-07-26
> **merlinus said:**
> This might work:

title        Windows 
rootnoverify    (hd2,4)
[B]map (hd0) (hd2)
map (hd2) (hd0)[/B]
savedefault
makeactive
chainloader    +1

Also, make sure hd2 is listed in /boot/grub/device.map:
(hd2)  /dev/sdc

Yea, that looks closer. :)

---

### Post by mayagamer on 2009-07-26
Thanks to you all.

if I take this usb drive to another machine,(hd*,4) may be not the right partition.Am I right?

---

### Post by merlinus on 2009-07-26
It will still be on the same partition (4), but not necessarily the same hdd number.  It would depend upon the other computer's hdd setup.

For example, if that machine had only one hdd, then windows would be (hd1,4).

---

### Post by mayagamer on 2009-07-26
> **merlinus said:**
> It will still be on the same partition (4), but not necessarily the same hdd number.  It would depend upon the other computer's hdd setup.

For example, if that machine had only one hdd, then windows would be (hd1,4).

so why not use uuid ?
like this
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		3ca6b9ce-7708-4b5e-9145-69ceb9702796
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=3ca6b9ce-7708-4b5e-9145-69ceb9702796 ro locale=zh_CN quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
```

---

### Post by Bucky Ball on 2009-07-26
> **mayagamer said:**
> so why not use uuid ?
like this
```
title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        3ca6b9ce-7708-4b5e-9145-69ceb9702796
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=3ca6b9ce-7708-4b5e-9145-69ceb9702796 ro locale=zh_CN quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet
```

Cos OP trying to boot Windows.

---

### Post by Bucky Ball on 2009-07-26
That is correct. If the machine you want to use it on has a different number of hard drives than your own you could find some problems. Plug it into another machine, set bios to boot from external USB drive and see what happens. Might give you a clue as to how to fix it. If it boots to grub on the external drive, great. But if so, the internal drives probably won't be automounted; you may have to do that manually.

---

### Post by mayagamer on 2009-07-26
I find it.
the third partition is a logical partition.
I turned it to primary partition,and it works!

thank you!

---

### Post by Bucky Ball on 2009-07-27
Excellent news, mayagamer. Windows won't love any place else. Basically, rule of thumb: Windows goes first partition (primary) then you can make an extended patition with the rest and put what you want in there (and unlike primary partitions, within an extended one you can have way more than four paritions on a drive). As you have found, there are other ways, but for simplicity, it is worth doing it this way unless there is a specific reason to not.


> **merlinus said:**
> 

For example, if that machine had only one hdd, then windows would be (hd1,4).

(hd1,4) = sdb5. Second hard drive (hd1), fifth partition (hd1,**4**)

If the machine had one hard drive that drive would be (hd0) = sda. :)

---

