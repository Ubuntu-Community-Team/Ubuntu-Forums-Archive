---
title: "FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap"
date: 2011-06-13
forum: General Help
---

### Post by SIE on 2011-06-13
Hello all!

I was going to install Ubuntu 11.04 last weekend and decided to use my GParted live CD to prepare my hard drive beforehand. I dual boot with Windows 7 and only wanted to format my /, /home, and /swap partitions for a clean Ubuntu install. I then installed Ubuntu 11.04 and restarted. GRUB gave me this error upon restarting: "FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap"

I'm not sure what went wrong, since I have done the exact same steps with Gparted and Ubuntu before. Any help or suggestions to fix my boot process would be greatly appreciated!

Here is the output of my "fdisk -l", if that helps. I have 3 NTFS partitions (100Mb boot sector, OS, Data) in addition to a /, /home, and swap partition.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0a9794b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
/dev/sda2          206848   252110847   125952000    7  HPFS/NTFS
/dev/sda3       252124110   273603014    10739452+  83  Linux
/dev/sda4       273603076  1953520064   839958494+   5  Extended
/dev/sda5       277508096  1904101375   813296640    7  HPFS/NTFS
/dev/sda6       273603141   277506809     1951834+  82  Linux swap / Solaris
/dev/sda7      1904104188  1953520064    24707938+  83  Linux

Partition table entries are not in disk order
```

---

### Post by srs5694 on 2011-06-14
Your partitions look OK to me, but it's conceivable that I'm missing something. (Reading and comparing large numbers is, after, all the forte of computers, not of humans.) A few ideas occur to me about what might be causing the problem:


[list]
[*]I've missed something and there's really some partition overlap.
[*]A bug in GRUB causing it to issue a false alarm.
[*]Data corruption in GRUB (in the MBR, the post-MBR sectors, or a file in Linux) could be causing it to issue a false alarm. This seems like a long-shot, though; data corruption would be more likely to cause GRUB to crash.
[*]A corrupted filesystem or swap data. If the /dev/sda3 (Linux, presumably ext4fs; this is the partition that immediately precedes /dev/sda6 on disk) or /dev/sda6 (swap) data structures are corrupt, they could be larger than the containing partition and might therefore be triggering an alarm in GRUB.
[*]Some hidden partition data might be causing GRUB to flake out. CHS values, for instance, are normally hidden by fdisk, since they aren't useful on disks or partitions above about 8 GB. If those values are odd, though, it's conceivable that GRUB is using them and getting confused.
[*]A hardware fault. Such problems cause all sorts of weird symptoms, and this bug would not be the weirdest I've heard of.
[/list]


As to how you should proceed, I recommend the following:


[list=1]
[*]Back up all the important data from the disk. Since you've just re-installed Linux, you shouldn't need to bother with the Linux data, but Windows is another matter....
[*]Run a SMART utility, such as smartctl, GSmartControl, or Palimpsest Disk Utility, on the disk. Look for problems such as reallocated sectors. GSmartControl and Palimpsest highlight most problems in red so they're easy to spot. You might also run an active disk check. A short check takes just a couple of minutes to run, but a longer check can take hours. If you spot problems, post back and look into your disk's warranty terms.
[*]Run [FixParts](http://www.rodsbooks.com/fixparts/) on the disk. When you type "p", if it reports that it's omitting any partitions, then I've missed something when I looked for overlapping partitions. Post back with details or proceed at your discretion. Even if FixParts doesn't report errors, you could try saving your partition table with "w". That will recompute the CHS values (which should mostly be maxed out) and rewrite some other low-level data structures, which might fix some hidden problems.
[*]Run fsck on /dev/sda3 using a Linux emergency disc or the Ubuntu live CD. If it reports problems that it can't correct, and especially if fsck reports that the filesystem is too big for the partition it's in, don't do anything more from this list; you'll need to take a different course to recover from this problem.
[*]Use mkswap or GParted to re-create the swap space on /dev/sda6 (which is likely to become /dev/sda5 if you run FixParts on the disk, so be sure to check that you're creating fresh swap space on the correct partition!). If you do this, you'll need to update the swap space's UUID in /etc/fstab.
[*]In Windows, run CHKDSK on /dev/sda5 (which is likely to become /dev/sda6 if you run FixParts, although this Linux designation won't matter in Windows).
[*]Re-install GRUB. You can do this from the Ubuntu live CD or in various other ways.
[/list]


You probably won't need to do every one of these things, and aside from #1, the order is somewhat arbitrary. If something seems to produce positive results, you can stop the procedure there.

---

