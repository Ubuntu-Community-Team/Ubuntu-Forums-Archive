---
title: "External Harddrive Read Only"
date: 2012-01-03
forum: General Help
---

### Post by elliottryan on 2012-01-03
Hey all,

I have a Toshiba External Hard Drive (ntfs) that I had purchased, plugged in and was transfering files when I accidentally bumped it loose. Ever since then it will mount but will only mount as Read Only and when I try to change permissions it  just says "error setting permissions:Read-only file system" I am going insane. I feel like I am missing something very simple. Any help would be appreciated.

Thanks!

---

### Post by josephmills on 2012-01-03
Hi there could you plug in the ex.harddrive and  open your terminal (ctrl + alt + t ) then enter the commands ```
sudo fdisk -l
``` then paste here. thanks also have you thought about making it ext3/4 ? with something like gparted if this all sounds foreign then just say so and I sure that some one iof not me will shine in. 
thanks

---

### Post by elliottryan on 2012-01-03
Here's what I get:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cc07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   952197119   476097536   83  Linux
/dev/sda2       952199166   976771071    12285953    5  Extended
/dev/sda5       952199168   976771071    12285952   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa05b6f4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976771119   488384536    7  HPFS/NTFS/exFAT
```I opened up Gparted and I am not even sure if it sees the external... I have been using Ubuntu for over a year now but this is the first issue I've had with it so this stuff is a little new to me.

---

### Post by josephmills on 2012-01-03
```
sudo mount /dev/sdc1/ /mnt/ 
```
then 
```
cd /mnt && ls -al 
``` then paste that . 
thanks

---

### Post by elliottryan on 2012-01-03
```
rye@rye-MD7818U:~$ sudo mount /dev/sdc1/ /mnt/
mount: /dev/sdc1 already mounted or /mnt/ busy
mount: according to mtab, /dev/sdc1 is mounted on /media/Pictures
rye@rye-MD7818U:~$ cd /mnt && ls -al
total 8
drwxr-xr-x  2 root root 4096 2010-10-07 02:15 .
drwxr-xr-x 24 root root 4096 2011-11-25 18:46 ..
rye@rye-MD7818U:/mnt$ 
```

---

### Post by josephmills on 2012-01-03
> **elliottryan said:**
> ```
rye@rye-MD7818U:~$ sudo mount /dev/sdc1/ /mnt/
mount: [COLOR="red"]/dev/sdc1[/COLOR] already mounted or /mnt/ busy
mount: according to mtab, /dev/sdc1 is mounted on[COLOR="Red"] /media/Pictures[/COLOR]
rye@rye-MD7818U:~$ cd /mnt && ls -al
total 8
drwxr-xr-x  2 root root 4096 2010-10-07 02:15 .
drwxr-xr-x 24 root root 4096 2011-11-25 18:46 ..
rye@rye-MD7818U:/mnt$ 
```

```
cd /media/Pictures/ && ls -al 
```
this is where it is mounted all ready we could unmount it and mount it to wherever we like. but no need for that right now lets see the above command

---

### Post by elliottryan on 2012-01-03
```
rye@rye-MD7818U:~$ cd /media/Pictures/ && ls -al
total 8
dr-x------ 1 rye  rye  4096 2011-11-25 18:14 .
drwxr-xr-x 3 root root 4096 2012-01-03 16:58 ..
rye@rye-MD7818U:/media/Pictures$ 

```

---

### Post by MrSpike16 on 2012-01-03
When the ntfs file system is damaged, the drive (partition) is treated as read only to protect it but still allow you to retrieve undamaged files.  Unfortunately there is no message telling you this.

Windows will probably allow you to continue to read and write with the file system damaged.   

Check the drive's file system from Windows and don't forget to "Safely Remove" drive after.

Since the drive was been written to when it came unplugged, this maybe your problem.

---

### Post by fkasmani on 2012-10-19
Hello, I seem to be having the same problem and have gone through what been suggested above. Looks like my external drive's file system (NTFS) is corrupted 'cos the USB cable seems to be cutting out power to it at times when I accidentally touch the cable (most of the times I even get a kernel panic when I "safely remove the drive", but:
[LIST=1]
[*]how can I confirm that it's the file system having got corrupt and not something else?
[*]Is my data at risk?
[*]Since this is my data backup drive, gparted says I have about 130GB free - can I partition this so I have the 130GB as another filesystem and continue with backing up to the new partition?
[*]Is a damaged filesystem repairable without data corruption?
[*](appologies if I sound crazy here, but no harm asking) Is it possible to change the filesystem of the corrupted drive/partition?
[/LIST]

---

