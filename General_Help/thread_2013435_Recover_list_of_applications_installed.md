---
title: "Recover list of applications installed"
date: 2012-06-30
forum: General Help
---

### Post by Robbyx on 2012-06-30
I removed lightdb and as a result can not get into Ubuntu 12.04 I am therefore using the LiveCD in the following commands. 

I need to extract a list of installed programs in the crashed installation. What am I doing wrong, because I can not see the package.selections appearing in sdc? (What I aim to do is create a full list of installed files which I can read back into a fresh install using rsync.)

ubuntu@ubuntu:/$ sudo mount -t ext4 /dev/sda1 /mnt
 # ok as /dev/sda1 already mounted or /mnt busy
ubuntu@ubuntu:/$ sudo mount -t proc proc /mnt/proc
ubuntu@ubuntu:/$ sudo mount -t sysfs sys /mnt/sys
ubuntu@ubuntu:/$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:/$ sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:/$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo mkdir /media/sdc
root@ubuntu:/# sudo mount -t ext4 /dev/sdc1 /media/sdc
sudo dpkg --get-selections  "*" >/media/sdc/package.selections

I am not getting an error message, but I can not find the file in sdc1. I am using nautilus to find the file.

```
ubuntu@ubuntu:~$ sudo ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 300 Jun 30 20:38 .
drwxr-xr-x 6 root root 120 Jun 30 20:38 ..
lrwxrwxrwx 1 root root  10 Jun 30 20:39 036e794e-60ee-4a3b-b39b-118fe853cbef -> ../../sdb1
lrwxrwxrwx 1 root root  10 Jun 30 20:39 0a1df677-5413-4a7d-913a-41bb99a52374 -> ../../sdc1
lrwxrwxrwx 1 root root  10 Jun 30 20:39 2a72276a-b65d-4697-85ec-6fb180c027c2 -> ../../sda8
lrwxrwxrwx 1 root root  10 Jun 30 20:39 38c88a1a-3f0f-4769-b3a3-571c6fa7599e -> ../../sda1
lrwxrwxrwx 1 root root  10 Jun 30 20:39 445f4bad-8ff5-4155-ad32-40e422f72795 -> ../../sdd1
lrwxrwxrwx 1 root root  10 Jun 30 20:39 4ea4f26d-0c99-4918-a4ea-fcad426e97fc -> ../../sda5
lrwxrwxrwx 1 root root  10 Jun 30 20:39 7b859c36-c68d-408f-9425-de9f525f3c71 -> ../../sdd5
lrwxrwxrwx 1 root root  10 Jun 30 20:39 86290d05-e673-4310-9f3e-93af30cc13af -> ../../sdd6
lrwxrwxrwx 1 root root  10 Jun 30 20:39 b2df1606-77d7-4ec0-a8f8-509ad75cbce5 -> ../../sda6
lrwxrwxrwx 1 root root  10 Jun 30 20:39 bf20f3bf-54ca-4b00-9269-576e57f11fed -> ../../sdd7
lrwxrwxrwx 1 root root  10 Jun 30 20:39 E0D0-35DF -> ../../sdf1
lrwxrwxrwx 1 root root  10 Jun 30 20:39 e53a03ef-bf3c-4d2e-80ed-58a5baadd201 -> ../../sda7
lrwxrwxrwx 1 root root  10 Jun 30 20:39 eff6e720-d952-4289-8e3f-2d31e0c27888 -> ../../sda2

```

```
root@ubuntu:/# sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009df22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    61442047    30720000   83  Linux
/dev/sda2        61442048   143362047    40960000   83  Linux
/dev/sda3       143364094  1953523711   905079809    5  Extended
/dev/sda5       143364096   184324095    20480000   83  Linux
/dev/sda6       184326144   225286143    20480000   83  Linux
/dev/sda7       225288192  1941235711   857973760   83  Linux
/dev/sda8      1941237760  1953523711     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065305

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   488394751   244196352   83  Linux

Disk /dev/sdc: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008323c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   488394751   244196352   83  Linux

Disk /dev/sdd: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   114462719    57230336   83  Linux
/dev/sdd3       114464766   964815704   425175469+   5  Extended
/dev/sdd5       122849118   337364999   107257941   83  Linux
/dev/sdd6       337365063   964815704   313725321   83  Linux
/dev/sdd7       114464768   122847231     4191232   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3aa5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              32     4014079     2007024    c  W95 FAT32 (LBA)
root@ubuntu:/# 

```


Robin

---

### Post by matt_symes on 2012-06-30
Hi
```

ubuntu@ubuntu:/$ sudo mount -t ext4 /dev/sda1 /mnt
 # ok as /dev/sda1 already mounted or /mnt busy
ubuntu@ubuntu:/$ sudo mount -t proc proc /mnt/proc
ubuntu@ubuntu:/$ sudo mount -t sysfs sys /mnt/sys
ubuntu@ubuntu:/$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:/$ sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:/$ sudo chroot /mnt /bin/bash
root@ubuntu:/# [COLOR=Red]sudo[/COLOR] mkdir /media/sdc
root@ubuntu:/# [COLOR=Red]sudo[/COLOR] mount -t ext4 /dev/sdc1 /media/sdc
[COLOR=Red]sudo[/COLOR] dpkg --get-selections  "*" >/media/sdc/package.selections
```

Just a point to note, when you are root in the chroot you don't need to use sudo. 

dpkg --get-selections does not require elevated privileges in a normal install anyway.

> 
root@ubuntu:/# [COLOR=Black]sudo[/COLOR] mount -t ext4 /dev/sdc1 /media/sdc
[COLOR=Black]sudo[/COLOR] dpkg --get-selections  "*" >/media/sdc/package.selections

Is the above a typo ? Is it on 2 lines like this...

> 
root@ubuntu:/# [COLOR=Black]sudo[/COLOR] mount -t ext4 /dev/sdc1 /media/sdc
 [COLOR=Red]root@ubuntu:/[/COLOR]#[COLOR=Black]sudo[/COLOR] dpkg --get-selections  "*" >/media/sdc/package.selections

If not i think it will need to be.

If it is try running the dpkg command in the chroot alone without the redirection and see if you get the packages display in the terminal.

On its own line...

```
dpkg --get-selections  
```

Kind regards

---

### Post by Robbyx on 2012-07-01
Thank you very much for the response. I found the permissions on the files and drives difficult to use because some were locked or not recognised by liveCD. I finally managed to get the package selections to be saved in a place I could see it and I have put it onto a flash drive. I am now going to do a clean install.

Robin

---

