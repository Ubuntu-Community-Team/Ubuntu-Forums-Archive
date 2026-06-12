---
title: "Grub restarts to command prompt"
date: 2009-10-05
forum: General Help
---

### Post by o3rat on 2009-10-05
I'm running a notebook with a dual boot of Windows XP and Ubuntu. After the most recent linux-header update my notebook only boots to the "Grub>" prompt.

I've had this problem before and I was able to simply fix it by doing the following:

Grub> find /boot/grub/stage1
     (hd0,4)
Grub> root (hd0,4)
Grub> setup (hd0)
Grub> reboot.

The problem I am having now is that the above command sequence does not affect the the menu.lst. I did a "sudo fdisk -l" using the LiveCD and I have the following output:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4555    36588006    7  HPFS/NTFS
/dev/sda2            4556        9668    41070172+   f  W95 Ext'd (LBA)
/dev/sda3            9669        9729      489982+  82  Linux swap / Solaris
/dev/sda5            4557        9668    41062140   83  Linux


```It looks like the Linux partion is actually partion 5, but when I try to do "root (hd0,5)" grub responds with "Partition not found." 

After all this I went back into parition sda5 using the LiveCD and manually edited the menu.list replacing the parition with (hd0,4) and the correct linux-header files (2.6.28-15). Is there a way I can re-number sda5 to sda4 so grub can automatically update the menu.lst?


This was the orginally menu.lst

```

title        Ubuntu 8.04.1, kernel 2.6.24-23-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-23-generic root=/dev/sda5
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

```

---

### Post by lavinog on 2009-10-05
sda5 is just a label, it doesn't mean the 5th partition...if you delete it and create a new in its place, it will be called sda6.  You should really stick with what find /boot/grub/stage1 reports.

if there is a problem with grub can you post menu.lst?

---

### Post by oldfred on 2009-10-06
sda5 is in old grub (hd0,4)

You can use UUID's to boot in menu.lst and that eliminates partition renumbing issues if you change partitions. They can still change UUID if you do some major types of things but not normally. You can also use UUID or label in fstab. You assign a label to a partition and use that.

Use blkid or blkid -L for new ubuntus to see your UUIDs.

Entry in menu.lst is
UUID  asdfsdfasdfasdfas
instead of 
root  (hdx,y)

fstab info with examples:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

