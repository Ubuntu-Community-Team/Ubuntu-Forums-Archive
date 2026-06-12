---
title: "Setting up a second drive"
date: 2009-09-02
forum: General Help
---

### Post by jedispork on 2009-09-02
I've formatted my secondary (internal)drive to ex3 using gparted. It wont let me write to it or create folders.  Could someone please help me get this going or point me to a guide.

thanks

---

### Post by Lampi on 2009-09-02
If you create a new partition the kernel sometimes can't re-read the partition table unless you reboot once - it tells you so in a short message.

---

### Post by x33a on 2009-09-02
post the output of
```
cat /etc/fstab
```

and
```
sudo fdisk -l
```

---

### Post by P4man on 2009-09-02
you created the partition using gparted as **root**. As a result, root owns the partition. Take it back :)

```
sudo chown user:user /yourmountpoint/yourdisk
```

(replace user with your username and change the path accordingly)

---

### Post by jedispork on 2009-09-03
Still can't get it going. This is my first time using the linux command line so please be patient. under gparted the mount point shows up as /media/disk 

```
chown: cannot access `/media/disk/dev/sda': No such file or directory
```and 

```
# / was on /dev/sda5 during installation
UUID=83ce596f-56c6-455b-a01c-110b2ae3b08a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=94cadf06-c782-4788-9919-8886e078e023 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf909b1ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12749      121601   874357760   83  Linux
/dev/sda2               1       12748   102398278+   5  Extended
/dev/sda5               1       12224    98189217   83  Linux
/dev/sda6           12225       12748     4208998+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1cef1ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156286976    7  HPFS/NTFS

```

---

### Post by Zoot7 on 2009-09-03
> **jedispork said:**
> Still can't get it going. This is my first time using the linux command line so please be patient. under gparted the mount point shows up as /media/disk 

```
chown: cannot access `/media/disk/dev/sda': No such file or directory
```
Use dev/sda1 instead for the chown command posted above. ;)

---

### Post by scouser73 on 2009-09-03
> **jedispork said:**
> I've formatted my secondary (internal)drive to ex3 using gparted. It wont let me write to it or create folders.  Could someone please help me get this going or point me to a guide.

thanks

Hi, there's a set of instructions set out in this tutorial for mounting a drive:[[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by DJINNSeKo on 2009-09-03
You can see your secondary drive sdb has NTFS on its only partition sdb1. 
And by the way you have a wierd extended partition on sda.

So i guess you probably just messed up with gparted and didn't partition correctly.

---

### Post by jedispork on 2009-09-03
When I installed ubuntu I wanted it on my secondary hard drive that I also use for all my storage. I wanted to let windows keep the entire drive its on all to itself in case I break stuff. I wasn't sure how to manually setup and make the right size partitions for swap when I installed ubuntu so I went into windows under disk management and made 100 gb for ubuntu and partitioned the rest of the drive and left it raw. I did this so I could just use the option "use the largest free space" when installing.

Does it matter that linux is listed as installed under the extended parition? I used gparted to recreate the additional disk space and this is how everything looks now.

```
# / was on /dev/sda5 during installation
UUID=83ce596f-56c6-455b-a01c-110b2ae3b08a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=94cadf06-c782-4788-9919-8886e078e023 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

``````
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf909b1ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12749      121601   874361722+  83  Linux
/dev/sda2               1       12748   102398278+   5  Extended
/dev/sda5               1       12224    98189217   83  Linux
/dev/sda6           12225       12748     4208998+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1cef1ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156286976    7  HPFS/NTFS
```Still having this problem

chown: cannot access `/media/disk/dev/sda1': No such file or directory

---

### Post by DJINNSeKo on 2009-09-04
Then please clarify this, what you want to access is your second partition on your linux hard drive?

Or

You wanted to format your windows hard drive as ext3 and use it?

---

