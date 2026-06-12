---
title: "Access Windows (NTFS) partition in Ubuntu 10.10 Maverick"
date: 2010-12-16
forum: General Help
---

### Post by kedarkekan on 2010-12-16
Hello all,

I tried to search around for a way to access my windows partition from within Linux. I was unable to mount the same using "mount" command. I read of a tool "ntfs-config" as well, this too didn't work for me.


Please share if anyone out there has an idea on how we can access the windows partition (NTFS) from within Ubuntu 10.10 Maverick.

EDIT:

Few details :

> kedar@Latitude:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda5 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kedar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kedar)



kedar@Latitude:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7640a4d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   243224099   121612018+   7  HPFS/NTFS
/dev/sda2       243224100   446446349   101611125    7  HPFS/NTFS
/dev/sda3       446447616   450447359     1999872   82  Linux swap / Solaris
/dev/sda4       450449406   488396799    18973697    5  Extended
/dev/sda5       450449408   454447103     1998848   83  Linux
/dev/sda6       454449152   488396799    16973824   83  Linux



kedar@Latitude:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt/winc/
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?



kedar@Latitude:~$ sudo mount -t ntfs-3g /dev/sda2 /mnt/wind/
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Thanks

---

### Post by Verbeck on 2010-12-16
is it a wubi install or a partitioned dualboot?
post the output of *sudo fdisk -l *from a terminal

---

### Post by kedarkekan on 2010-12-16
It's a partitioned dual boot. 


kedar@Latitude:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7640a4d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15140   121612018+   7  HPFS/NTFS
/dev/sda2           15141       27790   101611125    7  HPFS/NTFS
/dev/sda3           27791       28040     1999872   82  Linux swap / Solaris
/dev/sda4           28040       30402    18973697    5  Extended
/dev/sda5           28040       28289     1998848   83  Linux
/dev/sda6           28289       30402    16973824   83  Linux

---

### Post by coffeecat on 2010-12-16
The easiest way to mount a NTFS partition is simply to look in the Places menu and click on the partition. However, if you look at the output of your mount commands you'll see:

> NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.And the same for sda2, which suggests that there is something wring with the filesystem on both partitions. Are you able to boot into Windows?

---

### Post by kedarkekan on 2010-12-16
Yes, I am happily able to login into Windows. Clueless of why it pops me with "NTFS signature missing" !

---

### Post by theozzlives on 2010-12-16
Boot Windows and run scandisk on both partitions.

---

### Post by coffeecat on 2010-12-16
> **kedarkekan said:**
> Clueless of why it pops me with "NTFS signature missing" !

Yes, that is odd. I've not come across that before with a NTFS filesystem that's obviously OK. What happens when you use the Places menu, or the left pane in Nautilus?

---

### Post by kedarkekan on 2010-12-16
@theozzlives, Scandisk isn't supported/available for Windows NT (2000, XP etc). Here are results for CHKDSK (it's not the same as MS-DOS)


C:\>chkdsk
The type of the file system is NTFS.
Volume label is System.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is verifying security descriptors (stage 3
Security descriptor verification completed.

 121612018 KB total disk space.
  19121964 KB in 53996 files.
     14768 KB in 4599 indexes.
         0 KB in bad sectors.
    129150 KB in use by the system.
     65536 KB occupied by the log file.
 102346136 KB available on disk.

      4096 bytes in each allocation unit.
  30403004 total allocation units on disk.
  25586534 allocation units available on disk.

C:\>d:

D:\Documents and Settings\305026329>chkdsk
The type of the file system is NTFS.
Volume label is Data.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is verifying security descriptors (stage 3
Security descriptor verification completed.

 101611124 KB total disk space.
  11270116 KB in 6149 files.
      2592 KB in 974 indexes.
         0 KB in bad sectors.
     76240 KB in use by the system.
     65536 KB occupied by the log file.
  90262176 KB available on disk.

      4096 bytes in each allocation unit.
  25402781 total allocation units on disk.
  22565544 allocation units available on disk.

@coffeecat, there is no reference to "Partition" in places menu.

---

### Post by coffeecat on 2010-12-16
> **kedarkekan said:**
> @coffeecat, there is no reference to "Partition" in places menu.

No, there won't be. If the partitions are mountable, they will be listed somewhere between 'Computer' and 'Network' or in a drop-out labelled 'Removable Media'. If the partitions have partition labels, they will be listed. Otherwise they'll simply be identifiable from the listed size.

---

### Post by Morbius1 on 2010-12-16
By any chance do you have the Windows partitions encrypted from within Windows?

Just trying to figure out how Linux could say they are bad and Windows thinks they are fine.

---

### Post by kedarkekan on 2010-12-16
@Morbius1, you are suspecting it right.

I have a Safeboot utility (not sure you heard of it ?), which encrypts the disk. 

But I have dual booted the machine, which first loads safeboot and then I chain load Linux from Windows loader (NTLDR).

I believe windows partition should have been decrypted as safeboot login was done prior to linux login?

---

### Post by kedarkekan on 2010-12-16
It looks that with an encrypted partition, there is no way I can access the windows partition from within Linux.
This was good learning lesson. Thank you all for your valuable inputs. Really appreciate all your help


Cheers!

---

