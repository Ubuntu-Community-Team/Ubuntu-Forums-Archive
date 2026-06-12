---
title: "Recovering Files using Live Disc"
date: 2009-10-30
forum: General Help
---

### Post by PostChache on 2009-10-30
Hi, I'm having trouble my Ubuntu won't start anymore and I'm going to do a fresh install but I need to recover some of the Documents on it and I don't know how. I can't move the files to a Flash Drive because it says Permission Denied. Any way to get this to work?

---

### Post by prem1er on 2009-10-30
After you booted to the live disk, have you already mounted the drive you are trying to recover?

---

### Post by PostChache on 2009-10-30
> **prem1er said:**
> After you booted to the live disk, have you already mounted the drive you are trying to recover?

Uh, I don't think so? How do I do that?

---

### Post by prem1er on 2009-10-30
open a terminal and post the output of

```
sudo fdisk -l
```

---

### Post by PostChache on 2009-10-30
> **prem1er said:**
> open a terminal and post the output of

```
sudo fdisk -l
```


```
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80f6ca86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 8019 MB, 8019509248 bytes
45 heads, 45 sectors/track, 7734 cylinders
Units = cylinders of 2025 * 512 = 1036800 bytes
Disk identifier: 0xd029e3a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4        7735     7827520    7  HPFS/NTFS

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16
ubuntu@ubuntu:~$ 
 
```

---

### Post by prem1er on 2009-10-30
> **PostChache said:**
> ```
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80f6ca86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 8019 MB, 8019509248 bytes
45 heads, 45 sectors/track, 7734 cylinders
Units = cylinders of 2025 * 512 = 1036800 bytes
Disk identifier: 0xd029e3a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4        7735     7827520    7  HPFS/NTFS

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16
ubuntu@ubuntu:~$ 
 
```

Ok, and you are trying to recover the files from you old linux partition? Do

```
sudo mount /dev/sda1 /path/to/your/desktop
```

where /path... is the location of your desktop.  The mount should show up on your desktop and you can copy the files you want.

---

### Post by PostChache on 2009-10-30
> **prem1er said:**
> Ok, and you are trying to recover the files from you old linux partition? Do

```
sudo mount /dev/sda1 /path/to/your/desktop
```where /path... is the location of your desktop.  The mount should show up on your desktop and you can copy the files you want.

It's still telling me permission denied D:

I did ```
sudo mount /dev/sda1 ~/Desktop
```

---

### Post by prem1er on 2009-10-30
After it is mounted 

```
sudo cp -r /files /Desktop/[name of directory]
```

---

### Post by PostChache on 2009-10-30
Some of the files still say permission denied

---

### Post by prem1er on 2009-10-30
On the files that won't copy, go into the directory that contains them and post the output of 

```
ls -lrt
```

---

### Post by PostChache on 2009-10-30
> **prem1er said:**
> On the files that won't copy, go into the directory that contains them and post the output of 

```
ls -lrt
```


Here you go

```
ls -lrt
total 40
drwx------ 2 1000 1000 4096 2009-08-30 01:01 Ubuntu
drwxr-xr-x 2 1000 1000 4096 2009-09-15 15:40 h4x5
drwxr-xr-x 2 1000 1000 4096 2009-09-16 22:08 Statistics
-rw-r--r-- 1 1000 1000   59 2009-10-05 07:29 Company
drwx------ 5 1000 1000 4096 2009-10-06 16:01 Sociology
drwxr-xr-x 2 1000 1000 4096 2009-10-16 19:47 WiiISO
drwxr-xr-x 5 1000 1000 4096 2009-10-25 10:08 Studies
drwxr-xr-x 4 1000 1000 4096 2009-10-27 18:38 BritLit
drwx------ 2 1000 1000 4096 2009-10-28 15:49 Philosophy
drwxr-xr-x 2 1000 1000 4096 2009-10-28 18:39 Español

```

---

### Post by prem1er on 2009-10-30
Ok, and which one of these directories isn't copying for you?

---

### Post by PostChache on 2009-10-30
> **prem1er said:**
> Ok, and which one of these directories isn't copying for you?

Sociology Philosophy and Studies

---

### Post by prem1er on 2009-10-30
Ok, do

```
sudo chmod o+wxr [dir]
```

to the directories that aren't working for you, then they should copy fine.

---

### Post by PostChache on 2009-10-30
> **prem1er said:**
> Ok, do

```
sudo chmod o+wxr [dir]
```to the directories that aren't working for you, then they should copy fine.

This is working :3! Thankyou, is there any way to make it do everything inside the folder though? I have 100's of files that are locked up.

---

### Post by prem1er on 2009-10-30
Yea sorry that is my fault. Use the -R parameter after chmod. It will do the command recursively.

---

### Post by PostChache on 2009-10-30
> **prem1er said:**
> Yea sorry that is my fault. Use the -R parameter after chmod. It will do the command recursively.


Thank you so much for your help! You've saved my GPA xD

---

