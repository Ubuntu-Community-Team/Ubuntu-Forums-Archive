---
title: "Mounting image made with ntfsclone..."
date: 2009-08-22
forum: General Help
---

### Post by r0g on 2009-08-22
Hi all,

I'm not able to mount an image I made over ssh with 'ntfsclone', below is a record of the whole session, can anyone see why this is failing?(probably me doing something dumb I know but what?) I'm pretty sure I imaged the partition, not the whole drive :-/  Note: host key checking stuff is a temporary workaround for something else, I can't see how that would affect anything though.

Cheers,

Rog.

-----session---------------------

ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no tb_ssh@192.168.1.65
Warning: Permanently added '192.168.1.65' (RSA) to the list of known hosts.
tb_ssh@192.168.1.65's password: 
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)


$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b5f6b5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5877    47206971    7  HPFS/NTFS
/dev/sda2            5878        7296    11398117+   5  Extended
/dev/sda5            5878        7230    10867941   83  Linux
/dev/sda6            7231        7296      530113+  82  Linux swap / Solaris

Disk /dev/sdb: 4005 MB, 4005560320 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02306f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         487     3911648+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(485, 254, 63) logical=(486, 250, 20)
$ exit
Connection to 192.168.1.65 closed.

r0g@steppa:~$ ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no tb_ssh@192.168.1.65 'sudo ntfsclone --save-image -o - /dev/sda1' > myntfspartition.img
Warning: Permanently added '192.168.1.65' (RSA) to the list of known hosts.
tb_ssh@192.168.1.65's password: 
ntfsclone v2.0.0 (libntfs 10:0:0)
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 48339931136 bytes (48340 MB)
Current device size: 48339938304 bytes (48340 MB)
Scanning volume ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7417 MB (15.3%)   
Saving NTFS to image ...
100.00 percent completed
Syncing ...

r0g@steppa:~$ mkdir tmp
r0g@steppa:~$ sudo mount -o loop -t ntfs-3g myntfspartition.img tmp
NTFS signature is missing.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by P4man on 2009-08-22
I just browsed through the ntfs clone man page, and saw this:

> 
The Special Image Format
It&#8217;s also possible, actually it&#8217;s recommended, to save an NTFS filesystem to a special image format. Instead of representing unallocated blocks as holes, they are encoded using control codes. Thus, the image saves space without requiring sparse file support. The image format is ideal for streaming filesystem images over the network and similar, and can be used as a replacement for Ghost or Partition Image if it is combined with other tools. **The downside is that you can&#8217;t mount the image directly, you need to restore it first.**

To save an image using the special image format, use the -s or the **--save-image** option. To restore an image, use the -r or the --restore-image option. Note that you can restore images from standard input by using &#8217;-&#8217; as the SOURCE file. 

Looks like you're using that, so you'll need to restore the image before you can mount it.

---

### Post by r0g on 2009-08-22
DOH!

Thanks, I spotted that about 10 minutes after I posted too... I'm trying without that option now, fingers crossed! :)

---

### Post by r0g on 2009-08-22
Pah!

It uses exactly the same amount of space as dd without that switch!

Useless :-(

---

### Post by wurvy on 2010-05-24
ls(1) shows it taking up that much space (the size of the entire volume), but the resulting image is a sparse file.  du(1) should report only the amount of space used.

---

### Post by r0g on 2010-05-25
Ah that's interesting, would have never thought to check with du, thanks :)

---

