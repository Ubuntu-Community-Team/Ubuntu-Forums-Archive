---
title: "initramfs"
date: 2009-08-03
forum: General Help
---

### Post by pirireis on 2009-08-03
Hello. I have a ubuntu 9,04 on notebook since 3 month. But last week After I updated the ubuntu. The computer was slowly. I restarted pc. But the ubundu didn't open. I have a initramfs errors
 I can open the ubuntu with Live Cd, And I have a importand document,:( I should rescue this document. I opened with Live cd but I didn't see this disk and I tried this code. I wait your advice. :confused: Thanks


```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07fe07fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2422    19446682+   f  W95 Ext'd (LBA)
/dev/sda2   *        2423        4863    19607332+  83  Linux
/dev/sda5               2        2422    19446651    7  HPFS/NTFS


```
```
                                  ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/windows
ubuntu@ubuntu:~$ dmesg | tail
[ 2518.592935] JBD: IO error reading journal superblock
[ 2518.592943] EXT3-fs: error loading journal.
[ 2518.595199] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 2518.595250] sd 0:0:0:0: [sda] Write Protect is off
[ 2518.595258] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2518.595331] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2518.595410] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 2518.595453] sd 0:0:0:0: [sda] Write Protect is off
[ 2518.595461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2518.595532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
```


```
                                  ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 2392577
/dev/sda2: Attempt to read block from filesystem resulted in short read günlük dosyas&#305; super blo&#287;u okunuyor
fsck.ext3: Attempt to read block from filesystem resulted in short read - /dev/sda2 için ext3 günlü&#287;ü denetlenirken hata olu&#351;tu
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.ntfs: yok
fsck: Hata 2: fsck.ntfs /dev/sda5 için çal&#305;t&#305;r&#305;l&#305;rken olu&#351;tu.
ubuntu@ubuntu:~$  
```

---

### Post by pirireis on 2009-08-08
I have a importand documents and I can't know ubuntu perfect. Please help me I have waited for 4 days

---

### Post by Lampi on 2009-08-08
your disk might have problem - could you run:

sudo smartctl -H /dev/sda

this will run a health check on your drive - if it passes like this

> === START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

then it's okay and the problem is only filesystem related - can be fixed with fsck

make sure you **DON'T** mount /dev/sda2 if you run a filecheck, then run it like this:

```
sudo fsck -vfC /dev/sda2
```

---

### Post by tommcd on 2009-08-08
First try to fix the initramfs errors. Are you able to boot to recovery mode in Ubuntu? You can choose recovery mode from the grub menu. If you do not see the grub menu when you bootup the computer, then hit the **Esc** key as the computer boots to see the grub menu, and then choose recovery mode.
To try to fix the initramfs, try running this from recovery mode:
```
sudo update-initramfs -u
```
and then reboot. See if you can then boot Ubuntu.
To mount Ubuntu from the live CD, try this:
```

sudo mkdir /media/ubuntu
sudo mount /dev/sda2 -t ext3 /media/ubuntu

```
However, your output of fsck indicates that the super block of your Ubuntu partition is corrupted. I'm not sure how to get around that.
If this fails, you may want to try a system rescue CD to rescue your document. This is a live CD that has a lot of data rescue tools:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by pirireis on 2009-08-08
I wrote sudo smartctl -H /dev/sda and it give this
```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED 			 		

```

then 
I wrote

```
 sudo fsck -vfC /dev/sda2 
``` but I receive same error 
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 2392577
/dev/sda2: Attempt to read block from filesystem resulted in short read günlük dosyas&#305; super blo&#287;u okunuyor
fsck.ext3: Attempt to read block from filesystem resulted in short read - /dev/sda2 için ext3 günlü&#287;ü denetlenirken hata olu&#351;tu

and tommcd I cant open recovery mode it give diffirent initramfs errors, it cant open

---

### Post by pirireis on 2009-08-08
and I wrote 
```

sudo mount /dev/sda2 -t ext3 /media/ubuntu 
``` and it give mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by pirireis on 2009-08-08
When I open recovery mode. It give 

```
(initramfs) [   104.056229] Clocksource tsc unstable (delta = -431107055 ns)
```

---

### Post by tommcd on 2009-08-08
If you can't boot to recovery mode, and if you can't mount the Ubuntu partition from a live CD, and if you can't even run a fsck on the partition from a live CD (with the partition unmounted, of course), then I am not sure how else you could fix this.
See is you can rescue your document with the system rescue CD.

---

### Post by Lampi on 2009-08-08
this looks really messed up ... well, usually you have several copies of the superblock

you find them with:

dumpe2fs /dev/sda2 | grep Superblock

Usually the first backup is placed at inode #8193

There are a few howtos on that topic in the web, but I think your on your own, can't help you there.

---

