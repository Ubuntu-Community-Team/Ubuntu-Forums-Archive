---
title: "Why does testdisk say my Structure is bad?"
date: 2011-02-07
forum: General Help
---

### Post by FancyBoy on 2011-02-07
Hi,

I recently installed windows 7 next to my ubuntu installation, I had to mess with partitions a bit to get it all to work, now I finally made it work, I can boot nicely from booth of them, but gparted doesn't show my partitions anymore (just says unallocated space), and when I try TestDisk to rewrite my partition table it says structure bad when I configure it as I like it.

```
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121602 255 63
     Partition               Start        End    Size in sectors
P HPFS - NTFS              0   1  1 13054 254 56  209728505
P Linux                 9790 192  3 16317 213 24  104857600
* Linux                16317 213 25 16330 149 11     204800
L Linux                16330 149 12 120071 145 10 1666598912 [Personal Files]
L Linux Swap           120071 177 43 121601  57 40   24571888
```The first partition is a windows 7 partition of 100 GB (NTFS), that I want as a Primary partition
The second one is my Ubuntu partition of 30 GB (ext4), that I want as a Primary Partition
The third one is my boot partition of 100 MB (ext3), that I want as a primary bootable partition
The fourth one is my files partition of 794 GB (ext4), that I want as a logical partition
The fifth one is my Swap partition of 11 GB, that I want as a logical partition.

Why is this not possible? Why is this structure bad, everything works ok atm, except that I can't change partitions or create new partitions because they're not recognized.

Please help me out.

Greets
Fancyboy

---

### Post by FancyBoy on 2011-02-07
bump :(

---

### Post by oldfred on 2011-02-07
Boot flags always go on windows primary partition. Grub does not use a boot flag, but some BIOS require a boot flag on a primary partition.

Do your partitions overlap? I am not as familar with reading testdisk output.

P HPFS - NTFS              0   1  1 [COLOR=Red]13054[/COLOR] 254 56  209728505
P Linux                 [COLOR=Red]9790[/COLOR] 192  3 16317 213 24  104857600

Start should not be before an end, unless it is a extended partition that is the container for all the logicals.

What does this show?

```
sudo fdisk -lu
```
or 
sudo sfdisk -luS /dev/sda

Ignore any cylinder boundry type errors.

---

### Post by FancyBoy on 2011-02-07
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068a3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280   83  Linux
/dev/sda2        62916608   262146047    99614720    7  HPFS/NTFS
/dev/sda3       262146048   262350847      102400   83  Linux
/dev/sda4       262350900  1953536129   845592615    f  W95 Ext'd (LBA)
/dev/sda5       262352896  1928949759   833298432   83  Linux
```

---

### Post by oldfred on 2011-02-07
That does not show anything wrong. What was testdisk saying was wrong?

---

### Post by FancyBoy on 2011-02-07
Well, just that the structure in the original post was bad, but the problem is that gParted doesn't show any partitions, it just says 'unallocated space'...

Disk utility shows everything correct.

---

### Post by FancyBoy on 2011-02-07
So how do I fix this?

---

### Post by srs5694 on 2011-02-07
Actually, there is a problem: The extended partition extends beyond the end of the disk -- it ends on sector 1,953,536,129, but the disk has only 1,953,525,168 sectors. See [my Web page on this topic](http://www.rodsbooks.com/missing-parts/index.html) for details and fixes. If you need more help, please post back here.

FWIW, TestDisk itself can create this problem, so its complaining about it is a bit ironic.

---

### Post by FancyBoy on 2011-02-07
> **srs5694 said:**
> Actually, there is a problem: The extended partition extends beyond the end of the disk -- it ends on sector 1,953,536,129, but the disk has only 1,953,525,168 sectors. See [my Web page on this topic]("http://www.rodsbooks.com/missing-parts/index.html") for details and fixes. If you need more help, please post back here.

FWIW, TestDisk itself can create this problem, so its complaining about it is a bit ironic.

You sir, are an angel, everything worked and everything is fine now, I can see all my partitions in gparted now, I thank you very much!

I'll be marking this as Solved then.

---

