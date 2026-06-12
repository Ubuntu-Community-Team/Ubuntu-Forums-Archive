---
title: "/dev/mapper/cryptswap1 doesn't contain a valid partition table"
date: 2012-03-22
forum: General Help
---

### Post by doogiekd on 2012-03-22
dear friends, 

i am wondering why the following appears when i run "sudo fdisk -l"

"Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table"

it appears to be indicating that cryptswap is not mounting.

(more below)

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb25ec62f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    40962047    20480000   27  Hidden NTFS WinRE
/dev/sda2   *    40962048    41166847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        41166848   325166847   142000000    7  HPFS/NTFS/exFAT
/dev/sda4       325167102   976771071   325801985    5  Extended
/dev/sda5       325167104   333555711     4194304    6  FAT16
/dev/sda6       333557760   968771583   317606912   83  Linux
/dev/sda7       968773632   976771071     3998720   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 4094 MB, 4094689280 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7997440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66b5e8b0

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


but when i run "sudo blkid | grep swap" i get the following, which appears to indicate cryptswap IS mounted:

"/dev/mapper/cryptswap1: UUID="6e13475b-6433-4a85-b4eb-b688ff2b7887" TYPE="swap"


and when i run "sudo ls -lA /home/username/" the following indicates my home folders are encrypted:

total 28
drwxr-xr-x 3 kenneth kenneth 4096 2012-03-15 13:04 .cache
-rw-rw-r-- 1 kenneth kenneth   26 2012-03-20 19:23 .dmrc
lrwxrwxrwx 1 root    root      33 2012-03-10 12:56 .ecryptfs -> /home/.ecryptfs/kenneth/.ecryptfs
drwx------ 4 kenneth kenneth 4096 2012-03-12 13:27 .gconf
-rw-rw-r-- 1 kenneth kenneth    0 2012-03-15 18:07 .mtab.fuseiso
lrwxrwxrwx 1 root    root      32 2012-03-10 12:56 .Private -> /home/.ecryptfs/kenneth/.Private
-rw-r--r-- 1 kenneth kenneth  122 2012-03-10 13:14 .profile
drwx------ 2 kenneth kenneth 4096 2012-03-21 02:19 .pulse
-rw------- 1 kenneth kenneth  256 2012-03-18 02:17 .pulse-cookie
-rw------- 1 kenneth kenneth   50 2012-03-20 19:23 .Xauthority

also results of "cat /etc/crypttab" indicate encryption is working:

administrator@earth:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3453       1196       2257          0         57        462
-/+ buffers/cache:        676       2777
Swap:         3904          0       3904
administrator@earth:~$ cat /etc/crypttab
# <target name>	<source device>		<key file>	<options>
cryptswap1 /dev/sda7 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

so what is the deal with fdisk -l indicating 
"Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table" ?
is something wrong here?

i get no startup messages at boot.
running dual boot ubuntu & windows 7...although win 7 is never used but i kept it on there b/c it came with it loaded on the computer :)

---

### Post by Paddy Landau on 2012-03-22
That is usually the encrypted swap partition, and as such will not have a partition table available to fdisk.

---

### Post by doogiekd on 2012-03-22
thank you!

now that is the answer i wanted to hear.

marking this as solved.

thanks again for responding - 

doogiekd

---

