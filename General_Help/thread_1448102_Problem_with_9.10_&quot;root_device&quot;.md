---
title: "Problem with 9.10 &quot;root device&quot;?"
date: 2010-04-06
forum: General Help
---

### Post by MattM11 on 2010-04-06
I'm currently triple-booting:
[INDENT]- Vista
- Ubuntu 9.10
- Ubuntu 10.04 (beta)[/INDENT]

Everything was working fine up until a few days ago. 

But then...

The first problem I noticed was that the Grub screen was flickering ("Auto adjust in progress" came up on the monitor). It wasn't enough to make selecting an option impossible, it's just never done that before.

The big problem, though, came when I tried to boot up Ubuntu 9.10 (which I've had on my computer for ages). The Ubuntu logo comes up, but then nothing happens for about a minute, followed by the following error message:

Gave up waiting for root device
- Missing modules (cat /pro/modules; ls /dev)
ALERT! /dev/disk/byuuid/4f743ef0-7a38-481e-613e-ceee3a70ba14 does not exist. Dropping to shell!

The only thing I can do then is physically reboot the computer.

This happens if I try either Recovery Mode or using the previous kernal as well.

Both Vista and Ubuntu 10.04 (beta) continue to work without problem.

Any idea what's happened? Should I just think about reinstalling 9.10? Or is there a way to fix it?

---

### Post by Calash on 2010-04-06
Can you go into your 10.04 install and give us the output of the following


sudo fdisk -l


You may also get some better information over in the development forum.  Most of the Beta support is going on over there.

My first guess would be to try and run a fsck on the 9.10 partitions and see if that clears up the issue.

---

### Post by MattM11 on 2010-04-06
Sudo fdisk -l turns up this:

[B]Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10103    81103195+   7  HPFS/NTFS
/dev/sda3           23255       30394    57352019    5  Extended
/dev/sda4           10104       23254   105635407+  83  Linux
/dev/sda5           23255       24470     9767488+  83  Linux
/dev/sda6           24471       29947    43993971   83  Linux
/dev/sda7           29948       30394     3590496   82  Linux swap / Solaris

Partition table entries are not in disk order[/B]

Fsck on the 9.10 / partition:

[B]fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: clean, 212593/610800 files, 915838/2441872 blocks[/B]

> You may also get some better information over in the development forum. Most of the Beta support is going on over there.

I considered that, but it looks more like a problem with 9.10 - I've had the 10.04 beta installed for over a week before this problem started, and that still loads up fine.

I could be wrong though.

---

### Post by Calash on 2010-04-06
Did you try a fsck -f to force it?

The only reason I suggested the beta forum is that 10.04 has some updates to grub that may be partly responsible for the problems you are seeing.

---

### Post by MattM11 on 2010-04-06
> Did you try a fsck -f to force it?

Not quite sure how to do that. I just ran fsck from the terminal in 10.04.

> 10.04 has some updates to grub that may be partly responsible for the problems you are seeing.

Ahh - that hadn't occurred to me. You might well be right about that.

Thanks.

---

### Post by john newbuntu on 2010-04-06
Did you happen to adjust any of the partitions?

Using the liveCD, inspect your /etc/fstab of the 9.1 partition and check that the uuids for the filesystems match up with the uuids that you get using 
sudo blkid -c /dev/null
So, essentially, mount the 9.1 partition using liveCD, chroot and access the /etc/fstab.
Please make a backup of /etc/fstab before you perform any changes.

You could even try replacing the uuids with the partition devices such as /dev/sda5 etc.
Run a sudo update-grub from lucid and see if anything improves.

---

### Post by Calash on 2010-04-06
fsck -f /dev/sda5

This should force it to check the partition again.

---

### Post by MattM11 on 2010-04-06
Calash,

That gets me:

[B]fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 212593/610800 files (0.2% non-contiguous), 915838/2441872 blocks[/B]

john newbuntu,

> Did you happen to adjust any of the partitions?

No - I installed 10.04 beta onto an existing partition that I was no longer using. 

I'll make a note of your suggestions and try the liveCD a bit later when I've got more time.

Thanks again to both of you.

---

