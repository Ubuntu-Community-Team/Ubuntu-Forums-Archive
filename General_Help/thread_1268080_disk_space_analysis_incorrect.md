---
title: "disk space analysis incorrect?"
date: 2009-09-16
forum: General Help
---

### Post by Rainbowsix on 2009-09-16
I used the command **df -h** and it gave this result.
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   16G  120G  12% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  220K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  160K  1.8G   1% /dev
tmpfs                 1.8G  432K  1.8G   1% /dev/shm
lrm                   1.8G  2.5M  1.8G   1% /lib/modules/2.6.28-15-generic/volatile


I'm sure all of us know that 16GB and 120GB does not result in 144GB. Where is the lost disk space?

UPDATE:
Disk usage analyzer gives a total of 143GB, 15.9GB used, and 127.1GB available. This is correct. Why does df give a different result?

---

### Post by TheStroj on 2009-09-16
use this command:
```
sudo fdisk -l
```
and let us know what it says.

---

### Post by Rainbowsix on 2009-09-16
Here are my results
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085725

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18966   152344363+  83  Linux
/dev/sda2           18967       19457     3943957+   5  Extended
/dev/sda5           18967       19457     3943926   82  Linux swap / Solaris


I also examined my results from Disk usage analyzer and they're actually not correct either. The files and folders listed only add up to 14.8GB. It's closer, but not correct.

---

### Post by TheStroj on 2009-09-16
Disk /dev/sda: 160 GB

/dev/sda1 * 1 18966 152344363+ 83 Linux
/dev/sda2 18967 19457 3943957+ 5 Extended
/dev/sda5 18967 19457 3943926 82 Linux swap / Solaris



/dev/sda1 = 152 GB
/dev/sda2 = 4 GB 
/dev/sda5 = 4 GB

152 + 4 + 4 = 160 GB

Hope this helps

---

### Post by sedawk on 2009-09-16
Funny:
The maths of my /boot partition are
101105=80537+15347 with plain "df" and
99M=79M+15M with "df -h".

Most likely they only count real data and
not the meta-data of the file system that
takes space too.

---

### Post by Rainbowsix on 2009-09-16
Thank you, but I don't think you all understand what I'm asking.
df -h says within the main partition, there are 144GB total, 120GB available, and 16GB used. Where are the missing 8GB?

---

### Post by drs305 on 2009-09-16
One thing often overlooked in Linux is that the system reserves 5% for it's own use use. This percentage can be changed with the *tune2fs* command with the "-m" switch, although doing so generally isn't needed (or probably recommended). Often this reserved space is not taken into consideration.

You can read about tune2fs in the man pages ("man tune2fs").

---

### Post by TheStroj on 2009-09-16
> **Rainbowsix said:**
> Thank you, but I don't think you all understand what I'm asking.
df -h says within the main partition, there are 144GB total, 120GB available, and 16GB used. Where are the missing 8GB?

This is the other 8 GB you're looking for:
/dev/sda2 18967 19457 3943957+ 5 Extended
/dev/sda5 18967 19457 3943926 82 Linux swap / Solaris

4GB + 4GB = 8GB

As I already said:

/dev/sda1 = 152 GB
[B]/dev/sda2 = 4 GB 
/dev/sda5 = 4 GB [/B]

Hope this helps.

---

### Post by Zimmer on 2009-09-16
File systems and software often list file sizes or free space in some mixture of SI units and binary units; unfortunately, they sometimes use SI prefixes to refer to binary interpretation - that is using a label of gigabyte or GB for a number computed in terms of gibibytes (GiB), continuing the confusion.

Since the early 2000s most consumer hard drive capacities are grouped in certain size classes measured in gigabytes. The exact capacity of a given drive is usually some number above or below the class designation. Although most manufacturers of hard disk drives and flash-memory disk devices define 1 gigabyte as 1000000000bytes, the computer operating systems used by most users (with the notable exceptions of Linux[1] and Mac OS X 10.6[2]) usually calculate size in gibibytes by dividing the total capacity in bytes (whether it is disk capacity, file size, or system RAM) by 1073741824, but report the result with the symbol GB. This practice can be a cause of confusion, as a hard disk with a manufacturer-rated capacity of 400 gigabytes may be reported by the operating system as only 372 GB.

---

### Post by DaithiF on 2009-09-16
> **TheStroj said:**
> This is the other 8 GB you're looking for:
/dev/sda2 18967 19457 3943957+ 5 Extended
/dev/sda5 18967 19457 3943926 82 Linux swap / Solaris

4GB + 4GB = 8GB

As I already said:

/dev/sda1 = 152 GB
[B]/dev/sda2 = 4 GB 
/dev/sda5 = 4 GB [/B]

Hope this helps.
Nope, I'm afraid this is wrong.  /dev/sda5 is an extended partition within /dev/sda2, ie. it is the same 4GB.
So /dev/sda1 = 18967 cylinders of 8,225,280 bytes each = 156,000,660,480 bytes.
and /dev/sda[2,5] = (19457 - 18967 ) cylinders x 8,225,280 = 4,030,387,200 bytes
These 2 together add up to the size of the drive, but as Zimmer explains the GB reported will be less than these due to the 1000 vs 1024 difference.

But anyway, back to the actual question about the missing 8GB on /dev/sda1.  The answer is as drs305 says, its reserved space.  To confirm & calculate the amount:
```
sudo tune2fs -l /dev/sda1
```
Look for 'Reserved block count:' and 'Block size:' lines, one multiplied by the other = the reserved space.  The % reserved is tuneable, as drs305 also pointed out.


/dev/sda

---

### Post by Rainbowsix on 2009-09-16
> **TheStroj said:**
> This is the other 8 GB you're looking for:
/dev/sda2 18967 19457 3943957+ 5 Extended
/dev/sda5 18967 19457 3943926 82 Linux swap / Solaris

4GB + 4GB = 8GB

As I already said:

/dev/sda1 = 152 GB
[B]/dev/sda2 = 4 GB 
/dev/sda5 = 4 GB [/B]

Hope this helps.

I set up 4GB as a swap partition myself. I'm not even talking about the hard drive as a whole, but only a single partition which is sda1.


Thank you, everyone. I didn't know the system reserves that disk space. This is solved.

---

