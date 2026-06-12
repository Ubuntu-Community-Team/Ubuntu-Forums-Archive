---
title: "Getting Bad magic number in super-block while trying to open /dev/sda1 error"
date: 2011-03-05
forum: General Help
---

### Post by sandeepthakurala on 2011-03-05
Hi,

First of all I am new to Ubuntu. I have dual boot system, I have windows and ubuntu on my box. Today I was trying to lookin for check disk kind of utility in ubuntu that we have in windows and I came across tune2fs command, but when I am running this command on my machine I getting following error.

"tune2fs 1.41.12 (17-May-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock."

Command I am running: sudo tune2fs -c 20 /dev/sda1.

Output of fdisk -l command:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       17526   110061161+   f  W95 Ext'd (LBA)
/dev/sda3           17527       19457    15510757+  12  Compaq diagnostics
/dev/sda5            3825       10682    55085792    7  HPFS/NTFS
/dev/sda6           10682       15232    36542460    7  HPFS/NTFS
/dev/sda7           15232       15356     1000448   82  Linux swap / Solaris
/dev/sda8           15356       17526    17430528   83  Linux


can someone help me out what is the issue? :confused:

---

### Post by JKyleOKC on 2011-03-05
The tune2fs utility only works on Linux filesystems; your /dev/sda1 is a Windows partition according to your posting. Try the command on /dev/sda8 instead -- but be extremely cautious about using any command that modifies a file system via sudo, unless you know exactly what it will do and are prepared for getting an unbootable machine if anything goes wrong!

It looks as if you are trying to change the disk-check interval from the default to 20 days. Is there any reason for doing so? With current filesystem design, the check takes only a few seconds unless it finds serious problems...

---

### Post by sandeepthakurala on 2011-03-09
sorry for replying late. Actually I was searching for a scan disk kind of utility for ubuntu and I find this command in some thread so I tried to use it but it did not worked. I tried use this command on my windows partition because my box is dual boot and I have ubuntu and windows7 both on my box but from when I started using ubuntu I did not used windows so few days back I thought to use windows but when I started it, it gave me a disk reading error so I thought if there is a way to scan my disk from ubuntu to check if there are some error exists in the disk that why I was searching for such command or utility.

thanks.

---

