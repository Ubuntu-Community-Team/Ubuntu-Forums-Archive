---
title: "Please Help - How to mount existing RAID set from LiveCD"
date: 2009-12-07
forum: General Help
---

### Post by apesa on 2009-12-07
Relativity new to ubuntu, I am on 9.10 running a Bios config'd bootable RAID set with 2 partitions / and /home on Ext4.  Trying to repair Grub, but can't get RAID set mounted. I have booted into the LiveCD, but sudo fdisk -l returns 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095863

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095863

```while dmraid -r shows

```
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdb: pdc, "pdc_hdbgeifbd", mirror, ok, 976562432 sectors, data@ 0
/dev/sda: pdc, "pdc_hdbgeifbd", mirror, ok, 976562432 sectors, data@ 0

```How do I return the correct path or formulate the correct path for the RAID set so I can mount it and get in to fix Grub?

I am new at running Ubuntu under this type of RIAD. If there is a better way like LVM please chime in and point me in the right direction. I am looking for a reliable filesystem that is mirrored.

Thanks in advance,
Pat

---

### Post by apesa on 2009-12-07
Ok, so I determined the correct path to the raid mirror, /dev/mapper/pdc_hdbgeifdb

Now the mount command is asking for the filesystem type

```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/pdc_hdbgeifbd /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~
```$ 

Any takers on how to determine the correct fstype?

Pat

---

### Post by tribaldata on 2009-12-07
Hi Pat, 

I think you need to use the "ext4" type since you using ext4

so something like : sudo mount -t ext4 /dev/mapper/pdc_hdbgeifbd /mnt

---

### Post by apesa on 2009-12-07
Thanks, I tried that earlier and got this

```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/mapper/pdc_hdbgeifbd /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_hdbgeifbd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$
```It must look different under DMRAID

---

### Post by tribaldata on 2009-12-07
Go into console and type in 

sudo dmesg | tail

And post the result here.

---

### Post by apesa on 2009-12-07
Thanks, I tried that earlier and got this

```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/mapper/pdc_hdbgeifbd /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_hdbgeifbd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$
```It must look different under DMRAID

Here is dmesg
```
[12203.683339] EXT4-fs (dm-0): VFS: Can't find ext4 filesystem
[14572.472020] EXT4-fs (dm-0): VFS: Can't find ext4 filesystem

```

---

### Post by tribaldata on 2009-12-07
[12203.683339] EXT4-fs (dm-0): VFS: Can't find ext4 filesystem
[14572.472020] EXT4-fs (dm-0): VFS: Can't find ext4 filesystem

That normally means that your filesystem on the RAID is not ext4

Could it be something else ???

Try to do this is terminal to determine your filesystem type

```
df -T
```

It should give you something like this

```
df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext3    37483560  14242560  21336900  41% /
tmpfs        tmpfs      250596         0    250596   0% /lib/init/rw
varrun       tmpfs      250596       252    250344   1% /var/run
```

Once you established the FS type you will be able to try mounting it.

---

### Post by apesa on 2009-12-07
Thanks again, here is the output of df -T, I am on LiveCD

```
ubuntu@ubuntu:/dev$  df -T. I am on LiveCD.

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
aufs          aufs     2025004     86276   1938728   5% /
udev         tmpfs     2025004       276   2024728   1% /dev
/dev/sr0   iso9660      707376    707376         0 100% /cdrom
/dev/loop0
          squashfs      681472    681472         0 100% /rofs
none         tmpfs     2025004       248   2024756   1% /dev/shm
tmpfs        tmpfs     2025004        60   2024944   1% /tmp
none         tmpfs     2025004        88   2024916   1% /var/run
none         tmpfs     2025004         0   2025004   0% /var/lock
none         tmpfs     2025004         0   2025004   0% /lib/init/rw
ubuntu@ubuntu:/dev$ 

```When I installed this last week it defaulted to ext4 and I was sure I accepted this. I looked becuase I ran an ext4 under 9.04 amd64 before and had problems with the FS. I did not verify it was due to ext4 vs ext3, but I was paying attention and am 99% sure I formatted the mirror with ext4. I only have this miror (2x500gb) drives in the machine.

I would rather struggle through this than re-install. At elast until I find I am out of options.. No better way to learn.

Thanks again, I really appreciate your time.

Pat

---

### Post by apesa on 2009-12-07
Still digging around and have another question. Looking at the output of:

fdisk /dev/mapper/pdc_hdbgeifbd -l

```
ubuntu@ubuntu:/$ sudo fdisk /dev/mapper/pdc_hdbgeifbd -l

Disk /dev/mapper/pdc_hdbgeifbd: 500.0 GB, 499999965184 bytes
255 heads, 63 sectors/track, 60788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095863

                    Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:/$  
```Is there a reason I don't see any info in the last line, ie. Device Boot Start End Blocks ID System?

???

Just trying to figure out why I can't mount this RAID set. All other examples of this command in these forums has information under that line.

Pat

---

