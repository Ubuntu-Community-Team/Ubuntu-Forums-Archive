---
title: "Custom partition layout for SSD?"
date: 2012-08-02
forum: General Help
---

### Post by ojdon on 2012-08-02
I will be replacing my hard drive in my laptop with a 60GB SSD. Swap usually isn't recommended on a SSD and I've read that you should use a ext2 partition of 256mb for /boot. 

I am considering using a custom compiled Linux 3.4 Kernel which has good changes for btrfs, but reading around it is recommend to still use ext4 for the / partition. 

Is there any partition recommendation on getting maximum performance out of a SSD?

Thanks!

---

### Post by Beacon11 on 2012-08-02
> **ojdon said:**
> Is there any partition recommendation on getting maximum performance out of a SSD?

Is performance defined in terms of speed, longevity, or data safety?

---

### Post by oldfred on 2012-08-03
You do not need separate /boot. You may want to consider use gpt partitioning as that is recommended by Arch.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

New partition tools set partition start points correctly. Just be sure to use newer gparted not an old copy.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

Since partitions will be small you can use ext4, but turn off journal. Supposedly some advantages to ext4 with journal off over ext2.
You still need discard for trim and noatime to reduce writes as settings in fstab.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)

---

### Post by Paqman on 2012-08-03
> **ojdon said:**
> I've read that you should use a ext2 partition of 256mb for /boot.

That's a bit of a strange recommendation. Where did you read that? Normally the only reason to have a separate /boot is if you're doing something weird with your partitioning or filesystems, simply using an SSD isn't a reason.

> 
Is there any partition recommendation on getting maximum performance out of a SSD?


Nope. The partitioning tools should handle alignment these days. There are some options for optimisation, but they don't relate specifically to partitioning. Things you could do:
[LIST=1]
[*]Edit your /etc/fstab so that your parttiions mount with the option **discard**
[*]Also have them mount with the option **noatime** instead of the default **relatime**
[*]Move /tmp and possibly others such as browser cache and /var/logs into ramdisks
[*]Use a swapfile instead of a swap partition or mount swap on a magnetic drive
[/LIST]
Personally I do 1, 3 and 4, but don't bother with 2. Some people also recommend using a non-journaling filesystem, but I think that's giving up too much for a negligible benefit on modern SSDs.

---

### Post by dcstar on 2012-08-03
> **Paqman said:**
> 
[LIST=1]
[*] ....
[*] ....
[*] ....
[*]Use a swapfile instead of a swap partition or mount swap on a magnetic drive
[/LIST]
Personally I do 1, 3 and 4, but don't bother with 2. Some people also recommend using a non-journaling filesystem, but I think that's giving up too much for a negligible benefit on modern SSDs.

There is no point whatsoever in using a swap file instead of a swap partition on a SSD because the Linux kernel automatically uses Discard on Swap partitions.

---

