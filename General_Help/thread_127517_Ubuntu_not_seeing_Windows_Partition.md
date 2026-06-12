---
title: "Ubuntu not seeing Windows Partition"
date: 2006-02-09
forum: General Help
---

### Post by mempf on 2006-02-09
My Ubuntu install is not seeing my Windows partitions.

I am dual booting Ubuntu and Windows with ubuntu on one harddrive and Windows on the other.

Ubuntu is on a IDE harddrive with Windows on a SATA.

How can I get the partitions to show up?

Thanks

---

### Post by Sutekh on 2006-02-09
Check out this great link
[Mounting Windows Partitions in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

### Post by mempf on 2006-02-09
I follow that but when I try and access the mount point it says i dont have the permissions to view it.

---

### Post by Sutekh on 2006-02-09
But you mounted it?  If you've cleared that hurdle then gaining access to view it is easy

```
sudo chmod -R 777 /<mount folder>
```
**chmod** - is the command to change modes of access to files/folders

The **-R** flag makes the chmod command filter thoughout all folders underneath the specified one

**777** gives read/write/execute permissions to the owner/group owners/everyone else.

Just replace **/<mount folder>** with the folder where you mounted the partition.

---

### Post by mempf on 2006-02-09
I did that and still its the same probelm

---

### Post by Sutekh on 2006-02-09
Oooh its NTFS? The windows partition?  Scrap the chmod command.

Whats the entry for the Windows partition in your /etc/fstab look like??
Just post the contents of
```
cat /etc/fstab
```

Is it similiar to this ? ? ?
```
/dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0
```

---

### Post by mempf on 2006-02-09
yes

---

### Post by Sutekh on 2006-02-09
Ok, well in that case you'll have to provide the output of
```
sudo fdisk -l
```
This will list all your partitions.

Then
```
cat /etc/fstab
```
This will show your mount options.

---

### Post by mempf on 2006-02-09
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3647    29294496   83  Linux
/dev/hda2           14570       14946     3028252+   5  Extended
/dev/hda5           14570       14946     3028221   82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       24320   113426932+   f  W95 Ext'd (LBA)
/dev/sda5           10200       22947   102398278+   7  HPFS/NTFS




# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0
/dev/sda1       /windows        ntfs    nls=utf8,unmask=0222    0       0

---

### Post by Sutekh on 2006-02-09
Ok it looks fine. 
Did you remount everything using
```
sudo mount -a
```

---

### Post by mempf on 2006-02-09
yep

---

### Post by Sutekh on 2006-02-09
Wow there you go I never realised it didn't work.  All this time I thought it was working, but I never tested it.

The only thing I can think of is to open a browser as root, using
```
gksudo nautilus
```
Then you can go reading the files.

EDIT: It works, but I shouldn't try reading code past my bedtime

---

### Post by aysiu on 2006-02-09
[QUOTE=mempf]
/dev/sda1       /windows        ntfs    nls=utf8,unmask=0222    0       0[/QUOTE] Copy and paste is always better than retyping. This should say **umask=0222**, not **unmask=0222**.

---

### Post by mempf on 2006-02-09
That worked!

Thanks!

---

### Post by lamego on 2006-02-09
The option should be "umask" not "unmask" as seen on your  fstab .

---

### Post by Sutekh on 2006-02-09
[QUOTE=aysiu]Copy and paste is always better than retyping. This should say **umask=0222**, not **unmask=0222**.[/QUOTE]
Last time I try to read code at midnight!  Thanks aysiu I was pulling my hair out!

---

