---
title: "NTFS Partition not mounting"
date: 2006-06-04
forum: General Help
---

### Post by Adanufgail on 2006-06-04
I've had to reinstall GRUB, and I accidenlity installed it to hdb1 (my NTFS drive) rather than hdb2 (Ubuntu root). When I booted, my NTFS partition did not show up. I tried to manually mount it but it said that it wasn't NTFS. The Windows Installer said it had uncorrectable errors. Is it gone? Because I have a lot of valuable data there. If I can at least get read-only I will burn it to DVDs.

Please Help!

---

### Post by mlind on 2006-06-04
Grub is usually installed on physical device's MBR, not on a partition.
Your data is there, but you should tell how did you install GRUB and did you use
FDISK utility at any point?

Repairing partition table shouldn't be hard task, but don't let windows do anything to
that partition or data may be lost. So don't boot in windows.

for correctly installing grub you should have probably done 
*sudo update-grub /dev/hdb*

Could you post the outputs of
```

df -h
sudo fdisk -l

```

---

### Post by Adanufgail on 2006-06-04
I installed GRUB using the Breezy Badger Setup Disk (grub-install /dev/hda1)

df -h
```
michael@Ghost:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2              88G  4.7G   79G   6% /
varrun                506M  128K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  120K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.15-23-686/volatile
/dev/hda1             112G   86G   27G  77% /media/windows
/dev/hdd              569M  569M     0 100% /media/cdrom1
```

sudo fdisk -l
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       26757   214925571    7  HPFS/NTFS
/dev/hdb2           26758       38307    92775375   83  Linux
/dev/hdb3           38308       38913     4867695   82  Linux swap / Solaris

```

---

### Post by mlind on 2006-06-04
create a temporary mount point on /mnt or /media
```

sudo mkdir -p /mnt/share

```

Does command produce error message?
```

sudo mount -t ntfs /dev/hdb1 /mnt/share

```

partition table looks okay to me..

You could also try re-installing grub on the device which is set first on BIOS
boot order (usually  device that contains windows C drive).

use *sudo update-grub /dev/hd**x***
where is either a or b

---

### Post by Adanufgail on 2006-06-04
michael@Ghost:~$ sudo mount -t ntfs /dev/hdb1 /mnt/share
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by mlind on 2006-06-04
It's probably best then to use XP's recovery console..

You could try if you get any hints about error by doing
*sudo fdisk /dev/hdb*
but don't write anything to partition table.

Xp's recovery console provides utilities 
[LIST]
[*]fixboot
[*]fixmbr
[*]chkdsk
[/LIST]

that should help you to fix the problem.
Info about recovery console is described on  [http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

I've used it myself twice to fix unbootable ntfs drive.

---

### Post by Adanufgail on 2006-06-04
chkdsk returns errors when I use it.
I'll try fixboot and fixmbr.

I'm not sure what to do once I ran sudo fdisk /dev/hdb so I just exited.

---

### Post by mlind on 2006-06-04
[QUOTE=Adanufgail]chkdsk returns errors when I use it.
I'll try fixboot and fixmbr.

I'm not sure what to do once I ran sudo fdisk /dev/hdb so I just exited.[/QUOTE]

yeah, if it doesn't complain something about partition table, just exit.
If it would have said there's something wrong about ntfs drive's ID, then we
could have get it fixed this way.

---

### Post by Adanufgail on 2006-06-04
well, I ran fixboot... and it said that the partition type was unrecoginzied. It tried using fat. I rebooted...and went straight to the grub console. I couldn't remember how to boot linux and I've been unable to boot windows for several days (which I posted about in another post with little success) so I'm using my Knoppix Live CD now.

---

### Post by Adanufgail on 2006-06-04
What should I do as I don't view using a Lvie CD as a permenant solution.

---

### Post by mlind on 2006-06-04
You must erase/reinstall GRUB from the drive's MBR which is first on boot order,
that's probably /dev/hda.

Boot on rescue mode using install cd, mount your root partition and run
update-grub /dev/hda

---

### Post by Adanufgail on 2006-06-04
I couldn't mount my root (hdb2) but I could mount my Windows (hda1). It doesn't matter because now I also don't have access to grub-install or grub-update

---

### Post by Adanufgail on 2006-06-04
I still have access in Knoppix to my first HD, but I'd like to know if anyone has an idea as to what's wrong with my 2nd partition (mlind suggested that the partition tables might be messed up).

---

### Post by Adanufgail on 2006-06-05
how would I go about correcting my partition tables?

---

### Post by Adanufgail on 2006-06-05
Here is how my Partition Tables look from a Knoppix Live CD

knoppix@ttyp0[knoppix]$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?      105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?           1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/hdb4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by Adanufgail on 2006-06-20
Is there any way to get the data off my ntfs drive? I have a few  friends with drives I could farm it out to and a lot of DVD-Rs.

---

