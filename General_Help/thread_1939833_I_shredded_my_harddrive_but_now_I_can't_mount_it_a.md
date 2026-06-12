---
title: "I shredded my harddrive but now I can't mount it anymore"
date: 2012-03-12
forum: General Help
---

### Post by alkal0id on 2012-03-12
I decided to wipe my external harddrive clean with this command:
```
sudo shred -vfz -n 3 /dev/sdb1
```but it was taking ridiculously long so I just cancelled it after about 5%. I can no longer mount the harddrive though. Ubuntu usually automatically detects external harddrives the second I plug them in. Not anymore. If I run fdisk -l, I can see the device but when I try to mount it, it tells me that it can't find it in fstab or something. When I run fdisk -l, heres what it says about the drive:
```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00c47f39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2    31008256   976760032+   7  HPFS/NTFS

```

When I try to mount it, heres what it says:
```
alkal0id@laptop:~$ sudo mount /dev/sdc1
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab

```

Theres nothing about my other external harddrive in the fstab but I can mount it fine. Any idea what the problem is?

---

### Post by sudodus on 2012-03-12
You have overwritten the first 5% of it, where the partition table is situated, so there is nothing to mount. But it should be OK to use gparted to make a new partition table with a master boot record (MBR) and partitions.

Gparted is on the Ubuntu install CD or USB drives, but you can also install it to your normal installed system using
```
sudo apt-get install gparted
```

---

### Post by alkal0id on 2012-03-12
Thanks a lot. I was getting a bit worried there that I had destroyed my harddrive. I have gparted but I realised that there was some data that I forgot to transfer on the drive. Would gparted be able to make that MBR partition without formatting the whole drive?

---

### Post by raja.genupula on 2012-03-12
hi you can recover the data please try this 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by sudodus on 2012-03-12
> **alkal0id said:**
> Thanks a lot. I was getting a bit worried there that I had destroyed my harddrive. I have gparted but I realised that there was some data that I forgot to transfer on the drive. Would gparted be able to make that MBR partition without formatting the whole drive?
So you want to recover data from it. That is a different thing. Try Testdisk or if that won't work, try Photorec. See the following link [[COLOR="Red"]_http://www.cgsecurity.org/wiki/TestDisk_Livecd_[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

---

### Post by winh8r on 2012-03-12
I would suggest using testdisk/photorec which both part of the same package


```
sudo apt-get install testdisk
```


more info on testdisk and photorec is here:

[http://www.cgsecurity.org/]("http://www.cgsecurity.org/")

Do not write anything to that drive if you want to attempt recovery from it.

---

### Post by alkal0id on 2012-03-12
Cheers.

---

### Post by Suparious on 2012-03-12
Although this may be a silly question, but do you have an entry in /etc/fstab for your /dev/sdc1 mount point?

---

### Post by CrimpJiggler on 2012-03-16
> **Suparious said:**
> Although this may be a silly question, but do you have an entry in /etc/fstab for your /dev/sdc1 mount point?
Heres whats in my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=5d40bf5d-8fe9-4128-9fa2-a2e5c08a1a4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
#UUID=fb8b8955-3d9f-4ff0-9591-967d66f1d139 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```I altered those UUIDs in case they are unique identifiers who my drives or something. If I put an entry for /sdc1 along with a mount point for it, would it try to mount it even though 5% of the drive has been wiped? Is that a bad idea?

EDIT: Now that I think of it, I would no idea how to actually do that so diregard what I said about putting in a new entry lol

---

### Post by sudodus on 2012-03-16
> **CrimpJiggler said:**
> Heres whats in my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=5d40bf5d-8fe9-4128-9fa2-a2e5c08a1a4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
#UUID=fb8b8955-3d9f-4ff0-9591-967d66f1d139 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```I altered those UUIDs in case they are unique identifiers who my drives or something. If I put an entry for /sdc1 along with a mount point for it, would it try to mount it even though 5% of the drive has been wiped? Is that a bad idea?

EDIT: Now that I think of it, I would no idea how to actually do that so diregard what I said about putting in a new entry lol

First: Are you the same guy as *alkal0id* or writing on behalf of him/her? In that case I would answer that I don't think you can mount a partition, where you have wiped the first 5%.

Furthermore: Have you decided if you want to recover anything from the partition, or maybe already tried it?

Finally: I you can't or don't  want to repair it, try to edit the partition table with ***gparted***.

---

### Post by alkal0id on 2012-04-04
> **sudodus said:**
> First: Are you the same guy as *alkal0id* or writing on behalf of him/her? In that case I would answer that I don't think you can mount a partition, where you have wiped the first 5%.

Furthermore: Have you decided if you want to recover anything from the partition, or maybe already tried it?

Finally: I you can't or don't  want to repair it, try to edit the partition table with ***gparted***.
Yeah I forgot I had that crimpjiggler account when I made this alkal0id one but I still had it saved in keepassx. Unfortunately I do need to recover something. Its a folder with all the websites and PHP scripts I've made so far. It wouldn't be stored in the first 5% of the drive I don't think.

EDIT: When I do a quick search, testdisk doesn't detect any partitions in the harddrive. Its a 1TB drive so God knows how long a deeper search would take. Should I just forget about the PHP scripts and reformat the drive?

---

### Post by sudodus on 2012-04-04
> **alkal0id said:**
> Yeah I forgot I had that crimpjiggler account when I made this alkal0id one but I still had it saved in keepassx. Unfortunately I do need to recover something. Its a folder with all the websites and PHP scripts I've made so far. It wouldn't be stored in the first 5% of the drive I don't think.

EDIT: When I do a quick search, testdisk doesn't detect any partitions in the harddrive. Its a 1TB drive so God knows how long a deeper search would take. Should I just forget about the PHP scripts and reformat the drive?
I suggest that you check on the internet, if the PHP scripts might be recognized by ***PhotoRec***. What kind of files are they? xml-files or plain text files? If you have other files (documents, zipped files, photos, video-clips etc), PhotoRec can recover them from the file data (but the name will be lost).

---

