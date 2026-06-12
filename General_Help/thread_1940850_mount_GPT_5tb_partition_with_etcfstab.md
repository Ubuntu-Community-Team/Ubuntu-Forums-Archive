---
title: "mount GPT 5tb partition with /etc/fstab"
date: 2012-03-14
forum: General Help
---

### Post by buffchick on 2012-03-14
how to mount GPT 5tb partition with /etc/fstab? I get the following error with:
fstab
```
/dev/sdb1       /mnt/storage    ext4    defaults        0       0
```fdisk
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 5394.7 GB, 5394722193408 bytes
255 heads, 63 sectors/track, 655870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147483647+  ee  GPT

```sorry about the screen shot. It's a DRAC and I'm too lazy to type it by hand.

[IMG]http://imagehost.phoenix-nest.com/?di=5133174638711[/IMG]

ubuntu 10.04 clean install. Am booting to sda. this is secondary drive space.

---

### Post by oldfred on 2012-03-14
Fdisk does not work with gpt drives, but has been updated to at least see that the drive is gpt.

You should use gdisk, if you want something from command line. I do not have large gpt partitions but all the small one's mount exactly the same as the MBR partitions.

sudo parted /dev/sdb unit s print
sudo sfdisk -l -uS
sudo gdisk -l /dev/sdb


GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by buffchick on 2012-03-14
yeah, the fdisk was more to show that it's there. gparted results though...
```
sudo parted /dev/sdb unit s print
Model: DELL MD3000 (scsi)
Disk /dev/sdb: 10536566784s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End           Size          File system  Name     Flags
 1      34s    10536566750s  10536566717s  ext4         primary

```
it still won't mount at startup. I can ```
sudo mount /dev/sdb1 /mnt/storage
``` and it works fine.

---

### Post by oldfred on 2012-03-14
Post fstab:

Is this an external drive that may just be slow coming up to speed?

---

### Post by buffchick on 2012-03-14
the whole fstab or just the important part? ```
/dev/sdb1       /mnt/storage    ext4    defaults        0       0
```

and yes, it's a Dell MD3000 external SAN connected via a SAS5/e controller card.

---

### Post by oldfred on 2012-03-14
I am just wondering if it is not fully up to speed. 

I think I have seen others mount external probably USB drives and they are slow. Not sure about your external SAN, then.

Is this from a cold boot & it works from warm reboot? Or if you do wait does it then work? 

Maybe the system does not load a driver before trying to mount the SAN and then fails? You could add a startup script so it is manually mounted after booting.

Startup script location:
/etc/rc.local

---

### Post by buffchick on 2012-03-15
I've never actually waited. I get too bored. It doesn't work on cold or warm boot. It does need the multipathing driver and the driver for the controller card before it can be mounted.

---

### Post by oldfred on 2012-03-15
If you wait and get consistent results then the driver is not loaded before the mounting. 

I would file a bug and use the work around of a script.

---

### Post by buffchick on 2012-06-21
Just FYI, it ended up being a conflict between my iscsi SAN and the SAN connected through the controller card.

---

