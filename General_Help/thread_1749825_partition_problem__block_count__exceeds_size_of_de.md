---
title: "partition problem:  block count  exceeds size of device"
date: 2011-05-04
forum: General Help
---

### Post by fairyvoice on 2011-05-04
Hi you guys:
Days before, I got some data on /dev/sda3 to backup, so I use dd to do that job
```
dd if=/dev/sda3 of=/dev/sda6
``` 
which lasts so long that I Ctrl+C it, then I mount /dev/sda6 in the disk utility tools, copy all staff in the directory mounted on /dev/sda3 to the directory mounted on /dev/sda6, then I confirmed the files, all went well, the I delete /dev/sda3 for other usage.

After rebooting, I could not mount /dev/sda6 any longer
```
root@Atlantis:~# mount /dev/sda6 /media/
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and the dmesg told me that: "EXT4-fs (sda6): bad geometry: block count 12207031 exceeds size of device (5124727 blocks)"
I don't know how it get "12207031" and "5124727" blocks, they are neither the size of /dev/sda6 nor the size of files that exists in /dev/sda6.

I believe it is the dd command i used that ruined the partition table or super blocks or what, and I searched around website but didn't get any luck,  for example , when i tried "resize2fs /dev/sda6 20498908" (20498908 is the exact size of /dev/sda6 got from fdisk), i got this
```
root@Atlantis:~# resize2fs /dev/sda6 20498908
resize2fs 1.41.12 (17-May-2010)
The containing partition (or device) is only 5124727 (4k) blocks.
You requested a new size of 20498908 blocks.

```
and other try like e2fsck gave similar thing that told me nothing they could do.

I believe data in this partition is still there, can anyone give me an solution to make this partition back to use?
Thanks in advance

---

