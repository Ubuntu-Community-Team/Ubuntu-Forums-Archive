---
title: "Overlapping partitions. Can this be fixed?"
date: 2010-09-10
forum: General Help
---

### Post by atscott01 on 2010-09-10
I want to be able to run my windows 7 installation with virtualbox in ubuntu, but when I createrawvmdk I get the error overlapping partition description areas. I have run fdisk -l and get this output:
```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04ac1e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21165   170007615    7  HPFS/NTFS
/dev/sda2           21166       36987   127088641    f  W95 Ext'd (LBA)
/dev/sda3           36988       38914    15471448   12  Compaq diagnostics
/dev/sda5           33021       36987    31856514    7  HPFS/NTFS
/dev/sda6           21166       32533    91312128   83  Linux
/dev/sda7           32534       33021     3911680   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I really only have an ubuntu install and a windows 7 install, but for some reason there are 5 partitions. Is there a way I can fix this without losing data?

---

### Post by sandyd on 2010-09-10
> **atscott01 said:**
> I want to be able to run my windows 7 installation with virtualbox in ubuntu, but when I createrawvmdk I get the error overlapping partition description areas. I have run fdisk -l and get this output:
```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04ac1e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21165   170007615    7  HPFS/NTFS
/dev/sda2           21166       36987   127088641    f  W95 Ext'd (LBA)
/dev/sda3           36988       38914    15471448   12  Compaq diagnostics
/dev/sda5           33021       36987    31856514    7  HPFS/NTFS
/dev/sda6           21166       32533    91312128   83  Linux
/dev/sda7           32534       33021     3911680   82  Linux swap / Solaris

Partition table entries are not in disk order

```I really only have an ubuntu install and a windows 7 install, but for some reason there are 5 partitions. Is there a way I can fix this without losing data?
if you have overlapping partitions, fdisk should tell you that you have overlapping partitions.

Since fdisk did not display a message about overlapping partitions, I would disagree that there are actually overlapping partitions.

---

### Post by sandyd on 2010-09-10
> **atscott01 said:**
> I want to be able to run my windows 7 installation with virtualbox in ubuntu, but when I **createrawvmdk** I get the error overlapping partition description areas. I have run fdisk -l and get this output:
```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04ac1e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21165   170007615    7  HPFS/NTFS
/dev/sda2           21166       36987   127088641    f  W95 Ext'd (LBA)
/dev/sda3           36988       38914    15471448   12  Compaq diagnostics
/dev/sda5           33021       36987    31856514    7  HPFS/NTFS
/dev/sda6           21166       32533    91312128   83  Linux
/dev/sda7           32534       33021     3911680   82  Linux swap / Solaris

Partition table entries are not in disk order

```I really only have an ubuntu install and a windows 7 install, but for some reason there are 5 partitions. Is there a way I can fix this without losing data?
what? virtualbox uses vdi, not vdmk

---

### Post by atscott01 on 2010-09-10
> **sandyd said:**
> what? virtualbox uses vdi, not vdmk

For making a vm of an existing partition, VirtualBox uses vmdk: [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883).

> if you have overlapping partitions, fdisk should tell you that you have overlapping partitions.

Since fdisk did not display a message about overlapping partitions, I would disagree that there are actually overlapping partitions.

sda2 and sda6 seem to be overlapping. If there really isn't a problem, what can I do to solve the ```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 1 -relative -register
``` aborting because of overlapping partition areas?

---

### Post by srs5694 on 2010-09-10
> **atscott01 said:**
> sda2 and sda6 seem to be overlapping.

Since /dev/sda2 is an extended partition and /dev/sda6 is a logical partition inside that extended partition, this is perfectly normal. Note that /dev/sda5 and /dev/sda7 also reside within /dev/sda2; again, this is normal.

I didn't see any obvious problems; however, I might have missed something, and the default output you've presented, atscott01, shows partition start and end points using cylinder resolution, which isn't precise enough to be sure there are no problems. Try posting the output of "sudo fdisk -lu /dev/sda" -- note the extra "-u" parameter, which tells the program to use sector units rather than cylinder units.

---

### Post by john newbuntu on 2010-09-11
There is a cylinder overlap between sda7 and sda5 although this may not necessarily be a sector overlap.  If you notice, sda7 ends at 33021 where sda5 starts.  I'd say resize(reduce) sda7 by 1 cylinder (after turning swap off) and turn swap on again.

---

### Post by srs5694 on 2010-09-11
I would *not* try resizing partitions until after checking their sizes with sector precision, as described in my previous post. Making changes on a possibly damaged partition table without first understanding the nature of the damage could well end up making things worse.

---

### Post by john newbuntu on 2010-09-11
I agree with you partly srs.  The only reason why I did say resize was because it is a swap partition and I had encountered a similar situation before although this might well be a different one. So long as you not touch the beginning of sda5 you should be ok from a data recovery perspective.
But I certainly do value your opinion and personally would check the sector.

---

### Post by atscott01 on 2010-09-11
I resized the partitions after backing up the data and now get this from fdisk -l: 

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04ac1e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21165   170007615    7  HPFS/NTFS
/dev/sda2           21166       36987   127088641    f  W95 Ext'd (LBA)
/dev/sda3           36988       38914    15471448   12  Compaq diagnostics
/dev/sda5           33021       36985    31841310+   7  HPFS/NTFS
/dev/sda6           21166       32533    91312128   83  Linux
/dev/sda7           32534       33020     3911422   82  Linux swap / Solaris

Partition table entries are not in disk order

```

and this from fdisk -lu:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04ac1e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   340015292   170007615    7  HPFS/NTFS
/dev/sda2       340017150   594194431   127088641    f  W95 Ext'd (LBA)
/dev/sda3       594198528   625141423    15471448   12  Compaq diagnostics
/dev/sda5       530481404   594164024    31841310+   7  HPFS/NTFS
/dev/sda6       340017152   522641407    91312128   83  Linux
/dev/sda7       522643456   530466299     3911422   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I tried to run ```
sudo VBoxManage internalcommands createrawvmdk -filename ./Win7.vmdk -rawdisk /dev/sda -partitions 1 -register

```

but still got the error 
```
Overlapping partition description areas. Aborting
Error reading the partition information from '/dev/sda'
The raw disk vmdk file was not created

```

If you guys are as confused as I am as to why it is doing this, then I'll just leave it alone and simply restart into Windows (ugh) whenever I need to do Windows things.

Thank you for your help and consideration.

---

### Post by srs5694 on 2010-09-11
I don't see any overlapping partitions, but it's conceivable I've missed something. (Those long numbers just blur together! That's not a criticism, just a fact of dealing with disk sector numbers.) My suspicion is that the utility is getting confused by the out-of-order nature of your disk partitions. You can sort the partition order, to the extent that it's possible, by using fdisk; but there's a caveat: Sorting the partition order can sometimes confuse Linux and keep it from booting. This issue can be overcome by editing /etc/fstab and/or your GRUB configuration, or by re-installing GRUB.

If you want to risk sorting the partitions, type "sudo fdisk /dev/sda", then type "x" to enter the experts' menu, then type "f" to sort the order, then type "w" to save the changes. You should then reboot to be sure the computer still boots. Note that you won't be able to completely sort your partitions, since /dev/sda3, a primary partition, comes after /dev/sda2, the extended partition that houses your logical partitions (/dev/sda5, /dev/sda6, and /dev/sda7).

There may be a VirtualBox-specific solution to this problem, too, but I'm not familiar with VirtualBox, so I can't offer any suggestions along that line.

---

