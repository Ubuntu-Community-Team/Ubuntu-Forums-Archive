---
title: "Auto-mounting hard drive with /etc/fstab"
date: 2010-12-02
forum: General Help
---

### Post by laus_deo on 2010-12-02
I've been trying to auto mount my hard drive from the Window's partition so that it would be mounted every time I start Ubuntu, and everything I've seen says use the /etc/fstab file, but mine looks nothing like they show in these tutorials. Can anyone point me in the right direction on how to do this?

Heres what my /etc/fstab looks like. 


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0
# / was on /dev/sda5 during installation
UUID=ae6e05b2-bfaf-41ac-9ca0-a3cc7138df3a  /            ext4  errors=remount-ro    0  1
# swap was on /dev/sda6 during installation
UUID=d6bf38b2-d806-4226-b53d-f6969c5e7ece  none         swap  sw                   0  0
/dev/sdb1                                  /media/sdb1  vfat  defaults             0  0

---

### Post by karthick87 on 2010-12-02
Can you post the following outputs

```
sudo fdisk -l
```

```
sudo blkid
```

```
df
```

---

### Post by laus_deo on 2010-12-02
```
sudo fdisk - l

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track



```

```
sudo blkid

/dev/sda1: UUID="482ACC132ACBFC46" TYPE="ntfs" 
/dev/sda6: UUID="d6bf38b2-d806-4226-b53d-f6969c5e7ece" TYPE="swap" 
/dev/sda5: UUID="ae6e05b2-bfaf-41ac-9ca0-a3cc7138df3a" TYPE="ext4" 

```
```
df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            131002916  10076508 114271792   9% /
none                   1802112       316   1801796   1% /dev
none                   1806332      1784   1804548   1% /dev/shm
none                   1806332       196   1806136   1% /var/run
none                   1806332         0   1806332   0% /var/lock
none                   1806332         0   1806332   0% /lib/init/rw


```

---

### Post by karthick87 on 2010-12-02
If you are a beginner i will recommend you to use **ntfs-config **so that you can easily automount your drives in a click.

```
sudo apt-get install ntfs-config
```

After installation it will be found under [B]System>>Administration>>NTFS Configuration Tool
[/B]
[IMG]http://imgur.com/Zv6jH.png[/IMG]

Check your drives to automount and enable write support.

---

### Post by karthick87 on 2010-12-02
@laus_deo there should be no space..It's **sudo fdisk -l**

---

### Post by laus_deo on 2010-12-02
> @laus_deo there should be no space..It's sudo fdisk -l

oops, here that is just if you want to see it.

```
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e24561b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21638   173798400    7  HPFS/NTFS
/dev/sda2           21638       38914   138770433    5  Extended
/dev/sda5           21638       38207   133092352   83  Linux
/dev/sda6           38207       38914     5677056   82  Linux swap / Solaris

Disk /dev/sdb: 3963 MB, 3963617280 bytes
128 heads, 63 sectors/track, 960 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2         960     3866624    b  W95 FAT32


```

but the method you suggested worked perfectly. Thanks!!

---

### Post by karthick87 on 2010-12-02
You are welcome :) and JFI in your case if you want to add manually,you should add the following line in your fstab file.
> 
UUID=482ACC132ACBFC46    /dev/sda1    ntfs-3g    defaults,locale=en_IN    0    0

Mark this thread as solved.

---

