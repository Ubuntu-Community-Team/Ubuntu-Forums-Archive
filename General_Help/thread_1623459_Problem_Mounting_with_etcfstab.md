---
title: "Problem Mounting with /etc/fstab"
date: 2010-11-16
forum: General Help
---

### Post by dazman19 on 2010-11-16
Hi,

I am having a problem mounting 2 of my drives. Usually I just add a line in the /etc/fstab file to mount the drives on startup. It seems to work for one of my drives. But the other two hard drives are failing on startup. I can mount them manually once ubuntu has loaded.

Here is my /etc/fstab:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=6e6dd436-81d1-4d56-b00e-83790930658a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=84f89dbd-3a23-4547-ad87-855fd474b51e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdc1       /data                   ntfs    defaults        0       0
/dev/sde1       /multimedia          ntfs    defaults        0       0
/dev/sdd1	/installs		ntfs    defaults        0       0


the /data one mounts on startup, but the multimedia and installs fails and I dont understand why. do I need to chmod the folders /multimedia and /installs to allow for RWX? Because the only difference I can see is my data folder has different perm.


drwxrwxrwx   1 root root 16384 2010-11-15 08:56 data
drwxr-xr-x   2 root root  4096 2010-11-15 14:11 multimedia
drwxr-xr-x   2 root root  4096 2010-11-15 14:11 installs


don't ask me why the bytes size on the /data folder is different...

My devices are as follows:

sudo fdisk -l
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7854dedc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19458   156185600    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfd16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18850   151406592   83  Linux
/dev/sdb2           18850       19458     4881409    5  Extended
/dev/sdb5           18850       19458     4881408   82  Linux swap / Solaris

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9ae58afc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   42  SFS

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3d0a3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91202   732574583+  ee  GPT


Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      266306  2147483647+  ee  GPT

I still dont understand what I have done differently, that allows me to mount /dev/sdc1 correctly and does not work for /dev/sdd1 or /dev/sde1

---

### Post by oldfred on 2010-11-16
They are larger drives, perhaps they have not started up or started up in the same order from BIOS.

I would try using UUIDs rather than drive/partition to define drive.

sudo blkid
or 
ls -l /dev/disk/by-uuid/

And change fstab to use the UUID= style.

---

### Post by cinohpa on 2010-11-16
+1 for using uuids. Way more reliable.

Just out of curiosity, why are your permissions different on the other ntfs disks?

Have you been using this set up long? Have there been any recent changes? Did something break or were you trying to do something new?

I only ask because you can have problems trying to chmod directories/files on ntfs partitions the same way you can with extN partitions. The most reliable way around this is explicitly defining the permissions you need when you mount the drives. You may have luck specifying rwx explicitly at mount time.

You have to remember ntfs is a microsoft technology so you are working around microsoft to use ntfs with ubuntu, and there can be some funny hick ups to get things working.

---

### Post by dazman19 on 2010-11-16
sorry for being a bit nooby, but I am not sure how to use UUID in /etc/fstab, I have never needed to before as I have always mounted drives using the /dev/(name)

I am aware of this: 
 <file system> <mount point>   <type>  <options>       <dump>  <pass>
but to use UUID Do i do it this way?

Given:
> 
/dev/sda1: LABEL="System Reserved" UUID="8068EE0668EDFB34" TYPE="ntfs" 
/dev/sda2: UUID="A83CF1943CF15DAE" TYPE="ntfs" 
/dev/sdb1: UUID="6e6dd436-81d1-4d56-b00e-83790930658a" TYPE="ext4" 
/dev/sdb5: UUID="84f89dbd-3a23-4547-ad87-855fd474b51e" TYPE="swap" 
/dev/sdc1: LABEL="DataDrive" UUID="EAB0B00AB0AFDAF9" TYPE="ntfs" 
/dev/sdd2: LABEL="Installs" UUID="14FC2255FC223182" TYPE="ntfs" 
/dev/sde2: LABEL="MultiMedia" UUID="068C1F3A8C1F2429" TYPE="ntfs" 


I for /dev/sdd2 should change to?
UUID="14FC2255FC223182" /installs       ntfs    defaults    0  0

I dont want to damage any of the data... So just being sure...

---

### Post by cinohpa on 2010-11-16
Your syntax looks right. I mean it is consistent with the things already mounted by UUID in your fstab.

Just mounting drives shouldn't really be able to hurt anything anyways so don't worry about it too much.

---

### Post by yetiman64 on 2010-11-16
> **cinohpa said:**
> Your syntax looks right. I mean it is consistent with the things already mounted by UUID in your fstab.

Just mounting drives shouldn't really be able to hurt anything anyways so don't worry about it too much.

@ cinopha, note the quotation marks in 
> UUID="14FC2255FC223182" /installs       ntfs    defaults    0  0 may need to be removed or fstab may error, but the rest looks Ok.

---

### Post by cinohpa on 2010-11-16
Lol. You are right. Should be:

```

UUID=14FC2255FC223182 /installs ntfs defaults 0 0 

```

Sorry. Being lazy.

---

### Post by yetiman64 on 2010-11-16
> **cinohpa said:**
> Lol. You are right. Should be:

```

UUID=14FC2255FC223182 /installs ntfs defaults 0 0 

```Sorry. Being lazy.

:) That's Ok, its just fstab like terminal is extremely sensitive to so much as 1 character out of place usually.

Also when this entry is put in /etc/fstab, to test it before doing a reboot use in a terminal
```
sudo mount -a
```If no errors occur the partition will be mounted and accessible, if fstab has any errors the terminal will let you know about it OP rather than having a boot failure.

---

### Post by krismatth3 on 2010-11-16
```

UUID=14FC2255FC223182 /installs ntfs defaults 0 0 

```

That does not look like a valid UUID.

---

### Post by yetiman64 on 2010-11-16
> **krismatth3 said:**
> ```

UUID=14FC2255FC223182 /installs ntfs defaults 0 0 

```That does not look like a valid UUID.
It's a valid NTFS UUID, it is OK.

Edit: originally I had that same reaction here on seeing these style of UUIDs on NTFS partitions using gparted, they do work though :)

---

### Post by dazman19 on 2010-11-16
thanks for the replies. I dont really understand why I should use a UUID over my old method, but it seems most people are recomending mounting drives this way. So I will change all mine over.

Thanks for letting me know about the quotes.

Why is that not a valid UUID? I got that from typing:
sudo blkid

I am gonna go down for a reboot in a while, so hopefully this will rectify my problems.

---

### Post by yetiman64 on 2010-11-16
If you change your hardware configuration around for instance, the device allocation for a partition can change leaving fstab incorrect.

A UUID is fixed to a partition and will not change even if the hardware configuration changes, thus configuration changes won't affect fstab.

That is, UUIDs are a far more robust/stable means for mounting drives.

---

### Post by srs5694 on 2010-11-17
First, the problem fundamentally was because /dev/sdd and /dev/sde are GUID Partition Table (GPT) disks, but you were trying to use the partition numbers (1 in both cases) reported by the fdisk utility, which works only on Master Boot Record (MBR) disks. Changing to using UUIDs is a perfectly valid solution to the problem in this case, but of course you've got to find the UUID from the correct partition. Typing "sudo blkid" without specifying a partition will do this because it scans all the partitions; but note that the UUIDs you're using are for /dev/sdd2 and /dev/sde2, not the /dev/sdd1 and /dev/sde1 you used originally. Switching the numbers directly would work, too. If you need to learn what the partition tables on those disks *really* are, you must use parted or gdisk rather than fdisk. (Modern versions of fdisk even warn about its inability to handle GPT disks. Pay attention to such warnings! You've either trimmed them from your output or you're using a very old version of fdisk that lacks these warnings.)

Second, the "UUIDs" reported by blkid for NTFS partitions are *not* [true UUIDs,](http://en.wikipedia.org/wiki/Universally_Unique_Identifier) which are 128-bit numbers with a specific internal structure. In filesystems, UUIDs are used as a sort of serial number, the intent being to uniquely identify a given filesystem. Most Linux filesystems support UUIDs for this purpose, but FAT and NTFS don't; they use much shorter serial numbers instead. Because these shorter serial numbers serve the same purpose, blkid reports them as if they were UUIDs, and the mount command and /etc/fstab file enable you to mount these filesystems using the same UUID syntax as is used for real UUIDs, but specifying the serial number rather than the UUID. In short, the utilities should probably have used a more generic term, such as SERIAL, rather than UUID; but we're stuck with these tools' incorrect use of terminology.

---

