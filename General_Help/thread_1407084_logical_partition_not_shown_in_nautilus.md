---
title: "logical partition not shown in nautilus"
date: 2010-02-14
forum: General Help
---

### Post by planetLars on 2010-02-14
Hello,

I have a logical partition formatted with NTFS and created (from Windows) after Ubuntu 9.10 was installed. It's name is "Volume".

Now, it doesn't show under places nor nautilus. I think it is shown when using the Live CD again. It is shown in Volume Manager.

How can I have it show up next to my other partitions?

---

### Post by flippo on 2010-02-14
Is it mounted? if not, or if you don't know please post the output of both of these commands:

```
df -h
cat /etc/fstab
```

---

### Post by planetLars on 2010-02-14
> **flippo said:**
> Is it mounted?

It's not mounted. I can't see it that's why I can't mount it via nautilus :-) :-(.

```

lars@lars-desktop:~$ df -h
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/mapper/sil_bgacbicbfeae5
                       23G  3,6G   18G  17% /
udev                  2,0G  352K  2,0G   1% /dev
none                  2,0G  340K  2,0G   1% /dev/shm
none                  2,0G   88K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
none                   23G  3,6G   18G  17% /var/lib/ureadahead/debugfs
/dev/sdc1             233G  142G   91G  61% /media/WD PASSPORT

```

```

lars@lars-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sil_bgacbicbfeae5 /               ext4    errors=remount-ro 0       1
/dev/mapper/sil_bgacbicbfeae6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by darolu on 2010-02-14
Post what you get with this please:
```
$ sudo fdisk -l
```

---

### Post by flippo on 2010-02-14
bah, I gave you the wrong command, I really wanted the "sudo blkid" command.  To have nautilus recognize it I believe you have to add it to your fstab.  You can also automount it by adding it to your fstab, if you would like.  You can try to do it yourself (although be warned screwing up your fstab can create an unbootable system).  If you give me the output of ```
sudo blkid
``` I can also give you the fstab line you need.  

EDIT:  Oops, didn't see your post darolu, fdisk -l is also sufficient.

---

### Post by planetLars on 2010-02-14
I'm on a RAID0. I don't know whether fdisk works. Here you are:

```

lars@lars-desktop:~$ sudo fdisk -l
[sudo] password for lars: 
Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 5 korrigieren

Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x156866ff

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 endet nicht an einer Zylindergrenze.
/dev/sda2              13        5222    41840640    7  HPFS/NTFS
/dev/sda3            5223       38914   270630990    5  Erweiterte

Platte /dev/sdb: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000000

Festplatte /dev/sdb enthält keine gültige Partitionstabelle

Platte /dev/sdc: 250.1 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x5b6ac646

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

I hope everyrthing still works as it says something about correcting...

Here's blkid:

```

lars@lars-desktop:~$ sudo blkid
/dev/sda: TYPE="silicon_medley_raid_member" 
/dev/sdb: TYPE="silicon_medley_raid_member" 
/dev/mapper/sil_bgacbicbfeae1: UUID="C6E054E7E054DEED" LABEL="System-reserviert" TYPE="ntfs" 
/dev/mapper/sil_bgacbicbfeae2: UUID="1EEC7320EC72F17F" TYPE="ntfs" 
/dev/mapper/sil_bgacbicbfeae5: UUID="d94c457c-cd1e-4b54-af24-da4e55ad43a3" TYPE="ext4" 
/dev/mapper/sil_bgacbicbfeae6: UUID="B0FAE94DFAE91100" LABEL="Volume" TYPE="ntfs" 
/dev/mapper/sil_bgacbicbfeae7: UUID="29dd81d7-6d92-4f37-9be6-d3924d3107cf" TYPE="swap" 
/dev/sdc1: UUID="ECB2406EB2403EF8" LABEL="WD PASSPORT" TYPE="ntfs"

```

sil_bgacbicbfeae6 is the partition I want to be visible

---

### Post by flippo on 2010-02-14
Try appending the line:```
/dev/mapper/sil_bgacbicbfeae6 <mountdir> ntfs-3g users,defaults 0 0
```
to your fstab. Replace <mountdir> with the directory you want it mounted to, I usually to something like /media/Volume.  I believe you also have to make sure the directory exists and you should add the noauto if you don't want it automounted at bootup.

---

### Post by planetLars on 2010-02-14
Hello, thanks. According to "cat /etc/fstab" "sil_bgacbicbfeae6" is used already. sil_bgacbicbfeae6 was my swap partition originally. Now blkid shows sil_bgacbicbfeae7 as my swap partition and sil_bgacbicbfeae6 as the partition I created from Windows after Ubuntu was installed.
Doesn't this conflict?

I don't want to risk messing up my fstab. Do you have advice?

---

### Post by flippo on 2010-02-14
Hmmm, very good catch, I missed that entirely.  I have no idea whats going on there.  Either blkid is wrong, or your swap will corrupt to your ntfs drive if you use it.  Either way it doesn't sound like a very good situation atm.  I've never used raid, and I don't know any other tools to look at it.  It might be time for a good google search, unless someone else knows whats going on here.

---

### Post by flippo on 2010-02-14
Okay, alter some thought, and googling.  If I were in your shoes I would first turn off my swap (just in case) ```
sudo swapoff -a
```  Then I would try to mount /dev/mapper/sil_bgacbicbfeae7 and see what I get:
```
sudo mount /dev/mapper/sil_bgacbicbfeae7 <mountdir>
```
If it mounts as an ntfs filesystem, then blkid is acting strangely.  Otherwise, try mounting /dev/mapper/sil_bgacbicbfeae6.  If that is in fact your ntfs partition, you should really fix up your fstab.

Note: if neither of them will mount, your swap may have trashed your ntfs drive :-/ try mounting it in another OS.

---

### Post by planetLars on 2010-02-14
As Palimpsest also reports swap to be sil_bgacbicbfeae7 and 7 is the highest number and I think swap is always located at the disks end, I guess it's a good idea to modify fstab now to have swap be pointed to sil_bgacbicbfeae7.

Does anyone know about how partition number updates occur in Linux?

---

### Post by darolu on 2010-02-14
If my very limited knowledge of German is correct (aka google translate) this: Festplatte /dev/sdb enthält keine gültige Partitionstabelle means your disk sdb doesn't have a valid partitions table; is this by any chance the hard drive you can't mount?

Before assigning mount points with your fstab you first need to solve this partitions table, if it is indeed damaged, you may need to format it.

---

### Post by planetLars on 2010-02-14
@flippo sil_...6 is my NTFS partition. I'll fix fstab. Thanks for your help!

@darolu you translated correctly. However sdb is my second hdd in my RAID0. The partition I would like to mount is spanning the stripped disks.

Perhaps a bug has to be filed for the scenario here. If someone more knowledgeable could have a look..

Thanks all!

Wish me luck!

Lars

---

### Post by planetLars on 2010-02-14
I edited fstab.

I rebooted.

It worked out!

Now I just have to wait for the first time Swap is used.. :-)

Thanks again.

Lars

---

