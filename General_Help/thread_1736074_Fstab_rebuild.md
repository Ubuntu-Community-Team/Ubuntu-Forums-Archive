---
title: "Fstab rebuild"
date: 2011-04-22
forum: General Help
---

### Post by whynot on 2011-04-22
Hi
I have ubuntu 10.1 installed. I did by mistake some lines in /etc/fstab mess and now when i try to boot in login window it ask me always to press s key.Now is that any way to fix this error. Thanks.

---

### Post by lmarmisa on 2011-04-22
I suppose you are running Ubuntu Live CD.

Please, open a terminal, type these two commands and post the results:

```

sudo fdisk -l
sudo blkid

```

---

### Post by whynot on 2011-04-22
no i have installed in my computer not i have 2 operation systems Windows 7 and ubuntu from live cd installed.And sorry it was 10.10 i thing how can i examine it?
Thanks

---

### Post by lmarmisa on 2011-04-22
Please, boot your system from an Ubuntu 10.10 Live CD.

Then open a terminal (Applications -> Accessories -> Terminal), type these commands and post here the results:

```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```

Note: you can open Firefox while you run Ubuntu from the Live CD. So use copy & paste in order to post the results of the commands to this thread.

Best regards,

Luis

---

### Post by whynot on 2011-04-22
> **lmarmisa said:**
> Please, boot your system from an Ubuntu 10.10 Live CD.

Then open a terminal (Applications -> Accessories -> Terminal), type these commands and post here the results:

```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```

Note: you can open Firefox while you run Ubuntu from the Live CD. So use copy & paste in order to post the results of the commands to this thread.

Best regards,

Luis
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c2cd691

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         638     5120000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         638        9394    70332416    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9394       14594    41766912    f  W95 Ext'd (LBA)
/dev/sda5            9394       14594    41765888    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="RECOVERY" UUID="9417-721B" TYPE="vfat" 
/dev/sda2: LABEL="Windows7" UUID="448868AA88689C64" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="76C81E46C81E0551" TYPE="ntfs" 
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$
```

---

### Post by lmarmisa on 2011-04-22
It seems you installed the Wubi version of Ubuntu. Is it correct?.

The contents of the /etc/fstab should be:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by whynot on 2011-04-22
i guess so.I dont know very much but
Thank u.

---

### Post by lmarmisa on 2011-04-22
> **whynot said:**
> Hi
I have ubuntu 10.1 installed. I did by mistake some lines in /etc/fstab mess and now when i try to boot in login window it ask me always to press s key.Now is that any way to fix this error. Thanks.

Are you able to boot into Ubuntu (Wubi)?. What is the exact warning that is asking to press S?.

If you can run your Wubi Ubuntu, then open a terminal and type the command:

```

sudo gedit /etc/fstab

```

Then repair the file and save.

---

### Post by whynot on 2011-04-22
> **lmarmisa said:**
> Are you able to boot into Ubuntu (Wubi)?. What is the exact warning that is asking to press S?.

If you can run your Wubi Ubuntu, then open a terminal and type the command:

```

sudo gedit /etc/fstab

```

Then repair the file and save.

Ok now it works very well.Thanks a lot.

---

### Post by lmarmisa on 2011-04-22
Great.

Please, mark the thread as SOLVED.

---

### Post by whynot on 2011-04-22
> **lmarmisa said:**
> Great.

Please, mark the thread as SOLVED.

Sorry but i dont know how to do it? How do we do that?

---

### Post by lmarmisa on 2011-04-22
> **whynot said:**
> Sorry but i dont know how to do it? How do we do that?

[http://ubuntuforums.org/showpost.php?p=4527051](http://ubuntuforums.org/showpost.php?p=4527051)

---

### Post by whynot on 2011-04-22
> **whynot said:**
> Sorry but i dont know how to do it? How do we do that?

ok thanks

---

