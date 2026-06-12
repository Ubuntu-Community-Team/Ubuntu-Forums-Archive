---
title: "missing partition, &quot;can't have overlapping partition&quot;"
date: 2010-09-16
forum: General Help
---

### Post by jagfunk on 2010-09-16
I had 2 ubuntu installations and wanted to install xp along side, but it's gone horribly wrong. I would really appreciate any help.

before installation I had:
1 small fat partition (dell utility)
1 block unallocated space (for xp install)
1 extended partition with...
   --- 1 ubuntu 8.04 installation partition (ext3)
   --- 1 ext3 filesystem partition
   --- 1 swap partition (ext3)
1 ubuntu 10.04 installation partition

and I happily dual-booted between the 8.04 and 10.04.

The xp installation failed for some reason, said hal.dll was corrupt.

Booted a 10.04 live cd and tried to restore grub2, but couldn't find the 10.04 installation partition. Opened gParted and all I got was that the whole hard-drive was "unallocated" and the message "can't have overlapping partitions.

I restored grub (not grub2) and now have access to ubuntu 8.04 and my ext3 files partition.

But I can't access the 10.04 one and still have the same messages in gParted. I don't see overlapping partitions in fdisk.

```

$sudo fdisk -l
omitting empty partition (5)

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       17255   138544560    7  HPFS/NTFS
/dev/sda3           17256       45192   224403922    f  W95 Ext'd (LBA)
/dev/sda4           44060       45192     9100791   82  Linux swap / Solaris
/dev/sda5           17256       23629    51199123+  83  Linux
/dev/sda6           23630       44059   164103943+  83  Linux

```

so my 10.04 partition isn't even there. But I think it does show up using blkid (/dev/sda8 or 9 maybe?):

```

sudo blkid 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0B09" TYPE="vfat" 
/dev/sda2: UUID="1DE01B0468E743F6" LABEL="winxp" TYPE="ntfs" 
/dev/sda4: TYPE="swap" UUID="164229cf-a61b-471f-aa42-64da3c625fe2" 
/dev/sda5: LABEL="804root" UUID="ac4385f0-8061-4437-bf25-8dd8981e1fcc" TYPE="ext3" 
/dev/sda6: LABEL="804docs" UUID="1c359867-19b0-4568-a6bf-250ed4929e56" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="ac4385f0-8061-4437-bf25-8dd8981e1fcc" TYPE="ext3" LABEL="804root" 
/dev/sda8: UUID="89c07b84-07c3-4cbf-a7f3-688ce6c18281" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="ac4385f0-8061-4437-bf25-8dd8981e1fcc" TYPE="ext3" 

```

also I notice that my 8.04 root partition has been mounted twice.

I tried mounting /dev/sda9 but no luck:
```

sudo mount /dev/sda9 /mnt
mount: special device /dev/sda9 does not exist

```

would appreciate any help, I just really need a couple of the files on the 10.04 installation partition.

Thanks.

---

