---
title: "xp raid grub"
date: 2010-01-27
forum: General Help
---

### Post by Woody1987 on 2010-01-27
I have xp installed on a raid 0 and ubuntu on a separate disk. grub2 fails when it tries to add xp with this error:
```
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu lucid (development branch) (10.04) on /dev/sda2
Found Microsoft Windows XP Professional on /dev/mapper/isw_bbhjbdceed_Volume01
grub-probe: error: no mapping exists for `isw_bbhjbdceed_Volume01'
Found Microsoft Windows XP Professional on /dev/mapper/isw_bbhjbdceed_Volume0p1
grub-probe: error: no mapping exists for `isw_bbhjbdceed_Volume0p1'
done

```

I assume i need to edit /etc/default/grub to make this work but what exactly do i need to change?


fdisk:
```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c06d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+  83  Linux
/dev/sda2   *        6375        7783    11317792+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5d61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f4f1f4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121600   976751968+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

/dev/sda1 (ubuntu /)
/dev/sda2 (lucid /)
/dev/sdb1 (ubuntu /home)
/dev/mapper/isw_bbhjbdceed_Volume0 (covers /dev/sdc and /dev/sdd with XP)

---

### Post by meierfra. on 2010-01-27
Maybe  you just need to regenerated the device map:

```
sudo grub-mkdevicemap
sudo update-grub
```

---

### Post by Woody1987 on 2010-01-27
> **meierfra. said:**
> Maybe  you just need to regenerated the device map:

```
sudo grub-mkdevicemap
sudo update-grub
```

Didnt work

---

### Post by Woody1987 on 2010-01-30
anyone?

---

### Post by meierfra. on 2010-01-30
I don't think Grub1.97 works with Fakeraid. So you might have to revert to Legacy Grub.

---

### Post by Woody1987 on 2010-01-31
The raid was setup in the bios. Is that fakeraid?

---

### Post by meierfra. on 2010-01-31
```
The raid was setup in the bios. Is that fakeraid? 
```
As far  as I   understand (and I'm just starting  to learn about raid) a real raid (that is a hardware raid)  present itself to the Operating system and to grub just like a regular hard disk, it would get a  regular device name like /dev/sda and  Grub and the  OS do not need to treat the raid disk any different than a regular hard disk.

Since your raid disk   has a /dev/mapper device name, it should be fakeraid.   See  [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID) for some basic information.

Grub 1.97 does not seem to be able to handle fake  raid. Grub 1.98 is supposed to do better, but I  did some very limited testing with Grub 1.98 and didn't see any improvement. Burg is supposed to be even better, but  I haven't tried out Burg yet and there isn't much documentation. So I think reverting to Legacy Grub is your best option.

---

