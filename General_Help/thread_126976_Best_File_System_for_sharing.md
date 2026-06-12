---
title: "Best File System for sharing"
date: 2006-02-07
forum: General Help
---

### Post by aseem_mal on 2006-02-07
Hi. Here's what I am planning to do on my PC:

1. Install dual boot (Ubuntu and Win XP)
2. I want to partition my disk in 3 partitions. One each for Ubuntu and Win XP, and the third partition for sharing files among the two. A "free-for-all" partition. :)

My question is: What file system (ext3, fat32, ntfs) should I use for the common partition (the shared one). I want to make sure that I do not have any permissions related issues on this partition, irrespective of the OS that is accessing it.

I'll appreciate your suggestions/tips in doing the above setup.:-k 

Thanks,
A

---

### Post by byen on 2006-02-07
FAT32... all the way!!! that way you would have read and write access from windows as well as linux!

---

### Post by RAOF on 2006-02-07
You cannot use NTFS for your shared partition.  Ubuntu (and linux in general) can't write to it (safely/well).

Of the other two, FAT32 is probably the easiest.  You won't have any permissions problems, because it just doesn't support file permissions :).

EXT3 is a better filesystem - it's got a journal, so it is much less likely to lose data if the system crashes/the power goes out/ whatever.  It also supports file permissions, file metadata, all sorts of cool things.  It's linux native, but you can read/write to it from Windows with the ext2 drivers from [www.fs-driver.org](www.fs-driver.org).  

If you're moderately comfortable with a bit of fiddling, I'd try ext3 - it is a better filesystem.  If you want something that will just work(tm), FAT32.

---

### Post by DonPachi on 2006-02-08
I'm using ext3 as a shared partition.  The drivers mentioned above work superbly under winxp.

---

### Post by wilsonisme on 2006-02-08
nevermind- read the post incorrectly

---

### Post by nanotube on 2006-02-08
i use fat32 for my shared partition. fat32 does not support unix-style permissions, but other than that, it is just fine as a data drive. for more info, check out the link in my sig, and look at section "Setting up the dual boot system" and section "Mounting drives and /etc/fstab". 
in short, for fat32, you can set "whole drive" permissions, that all files in that partition will have. (eg, rwx for your user, and --- for everyone else).
like others said, ntfs cannot be reliably written to by linux. and i have not tried accessing ext3 from win...

---

### Post by nik on 2006-02-08
just remember that you will have problems with files > 4Gb on fat 32... And you should really consider making a separate /home partition for ubuntu.

---

### Post by aseem_mal on 2006-02-08
[QUOTE=nik]just remember that you will have problems with files > 4Gb on fat 32... And you should really consider making a separate /home partition for ubuntu.[/QUOTE]

Hi nik,
Can you please explain what you mean by making a separate /home partition for ubuntu? Thanks.:confused:

---

### Post by nik on 2006-02-08
Just that you put /home (which contains your files and desktop settings) on a partition by itself, which makes reinstalling a lot easier as you don't need to worry about backup.
My setup (pure ubuntu) is like this:

/ (10Gb ext3)
/home (about 29Gb ext3
/swap (1Gb swap)

this is on a 40 Gb harddrive. In addition I've got an external USB 60Gb disk, formatted as fat32 so I can hook it up to other (windows) computers.

To do this you need to select manual editing of partitions during setup.

Hope this helps :)

---

### Post by aseem_mal on 2006-02-08
Hi Nik. Just one more thing. I am forgetting the partition options during install. Is it true that during a manual partitioning, you can specify /home as a separate partition? I am vague about this.

Also, should one install Win XP before Ubuntu? Or it doesn't make a difference?

Thanks,
A

---

### Post by Robor on 2006-02-08
[QUOTE=aseem_mal]Hi Nik. Just one more thing. I am forgetting the partition options during install. Is it true that during a manual partitioning, you can specify /home as a separate partition? I am vague about this.

Also, should one install Win XP before Ubuntu? Or it doesn't make a difference?

Thanks,
A[/QUOTE]

Yes, you can create a separate partition for /home during the partitioning process.

Yes, you should install Windows XP first then Ubuntu after that.  Since you're doing that as plan rather than an afterthought it would probably be easier to specify a partition size during your WinXP install so you don't have to resize the NTFS partition to put Ubuntu on afterward.

---

### Post by nanotube on 2006-02-08
not to mention that if you install winxp second, it will overwrite your mbr and screw up the bootloader, so that you wont be able to boot into ubuntu without having to take trouble to restore grub. so definitely install win first.

---

### Post by aseem_mal on 2006-02-08
Thanks a bunch, all of you. I am so glad we have this forum to discuss such issues.

- Aseem

---

