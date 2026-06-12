---
title: "Missing menu.lst, among other GRUB issues..."
date: 2010-07-17
forum: General Help
---

### Post by iEthan on 2010-07-17
After installing Windows with Ubuntu previously installed, it killed my GRUB. I followed the GRUB restore tutorial ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)). Then, when that didn't work, I ran "update-grub" on it with a LiveUSB. It said it updated successfully, but when I checked for the menu.lst file, it still had not generated. I tried booting anyway, to be greeted with "grub>".

Then I ran this ([http://ubuntuforums.org/showpost.php?p=8647447&postcount=18](http://ubuntuforums.org/showpost.php?p=8647447&postcount=18)). I tried booting into the hard drive again, and nada. I went to go into the LiveUSB again and was greeted with the GRUB menu. I was able to boot into my Ubuntu install.

How could I generate my menu.lst file?

**Resources:**
fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10484    84212698+  83  Linux
/dev/sda2   *       10485       19131    69457027+   7  HPFS/NTFS
/dev/sda3           19132       19457     2618595    5  Extended
/dev/sda5           19132       19457     2618563+  82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b8f2aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1940     1955488+   b  W95 FAT32

```

fdisk -lu
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   168425459    84212698+  83  Linux
/dev/sda2   *   168425460   307339514    69457027+   7  HPFS/NTFS
/dev/sda3       307339515   312576704     2618595    5  Extended
/dev/sda5       307339578   312576704     2618563+  82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders, total 3911616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b8f2aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3911039     1955488+   b  W95 FAT32

```

---

### Post by Don1500 on 2010-07-17
> **iEthan said:**
> After installing Windows with Ubuntu previously installed, it killed my GRUB. I followed the GRUB restore tutorial ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)). Then, when that didn't work, I ran "update-grub" on it with a LiveUSB. It said it updated successfully, but when I checked for the menu.lst file, it still had not generated. I tried booting anyway, to be greeted with "grub>".

Then I ran this ([http://ubuntuforums.org/showpost.php?p=8647447&postcount=18](http://ubuntuforums.org/showpost.php?p=8647447&postcount=18)). I tried booting into the hard drive again, and nada. I went to go into the LiveUSB again and was greeted with the GRUB menu. I was able to boot into my Ubuntu install.

How could I generate my menu.lst file?

**Resources:**
fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10484    84212698+  83  Linux
/dev/sda2   *       10485       19131    69457027+   7  HPFS/NTFS   /dev/sda3           19132       19457     2618595    5  Extended
/dev/sda5           19132       19457     2618563+  82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b8f2aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1940     1955488+   b  W95 FAT32

```

fdisk -lu
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   168425459    84212698+  83  Linux
/dev/sda2   *   168425460   307339514    69457027+   7  HPFS/NTFS
/dev/sda3       307339515   312576704     2618595    5  Extended
/dev/sda5       307339578   312576704     2618563+  82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders, total 3911616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b8f2aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3911039     1955488+   b  W95 FAT32

```
I am assuming you are using 10.04. If so there is no Menu.lst, you have grub2, not grub.  This is a good thing.

go to gparted and remove the boot flag from sdb1 and sda2
put the boot flag on sda1

now go to terminal:
```
 sudo apt-get install grub
sudo update grub

```
restart and let me know the out come.

---

### Post by marshmallow1304 on 2010-07-17
Grub 2 does not use menu.lst.  Follow section 13 on [The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275").

---

