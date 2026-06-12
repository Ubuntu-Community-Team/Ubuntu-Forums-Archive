---
title: "Error splicing file: File too large"
date: 2011-12-27
forum: General Help
---

### Post by fayslr on 2011-12-27
I am copying a file, which has a size of 4.1 GB from my home folder to my portable usb drive formatted as ext4. When copying operation, reach at 4.0 GB, an error pops "Error splicing file: File too large". I know, that this error usually comes when you copy a file greater than 4 GB on fat32 disks, which has a limit of 4 gigs for the maximum file size, but i have no idea, why this error comes, when an ext4 formatted drive can hold a file upto 16 TB of size.

Can anybody help? I am using Ubuntu 10.04.

---

### Post by lukeiamyourfather on 2011-12-27
Dumb question, but is the partition big enough for the file?

---

### Post by fayslr on 2011-12-27
> **lukeiamyourfather said:**
> Dumb question, but is the partition big enough for the file?

Ofcourse! ... dude! ... it's 500 gigs external drive, ... almost emply ...

---

### Post by lukeiamyourfather on 2011-12-27
> **fayslr said:**
> Ofcourse! ... dude! ... it's 500 gigs external drive, ... almost emply ...

Hahaha, had to ask. Can you confirm that the partition is ext4? I believe you chose ext4 when formatting, but another question that needs to be asked.

```
sudo fdisk -l
```

---

### Post by cholericfun on 2011-12-27
Another wild guess: are you using a 32bit ubuntu?

---

### Post by Lil_Elvis on 2012-01-19
I am having the same issue.  fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7d3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19322   155202560   83  Linux
/dev/sda2           19323       19453     1044481    5  Extended
/dev/sda5           19323       19453     1044480   82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16131293184 bytes
25 heads, 25 sectors/track, 50410 cylinders
Units = cylinders of 625 * 512 = 320000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4       50411    15752192    c  W95 FAT32 (LBA)

---

### Post by mutley89 on 2012-01-19
> **Lil_Elvis said:**
> I am having the same issue.  fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7d3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19322   155202560   83  Linux
/dev/sda2           19323       19453     1044481    5  Extended
/dev/sda5           19323       19453     1044480   82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16131293184 bytes
25 heads, 25 sectors/track, 50410 cylinders
Units = cylinders of 625 * 512 = 320000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4       50411    15752192    c  W95 FAT32 (LBA)

Assuming /dev/sdb is your flash drive that  you are trying to write to,  it is formatted as FAT, which only allows files up to 4GB.  Backup any data on it and reformat as something else.

---

### Post by diacad on 2012-03-07
I am having the same problem. I tried to copy a 8 Gb .iso file from a system running 64 bit Ubuntu Studio 11.4 to a 500 Gb external USB drive formatted with NTFS, with 63 Gb space to spare on it. System has 8 Gb RAM. Hangs up with the "error splicing file: file too large " msg at 4 Gb. I can understand this with FAT, but not with NTFS. There must be something else going on here. Do you have to use an external drive formatted with ext4 (or something else - another poster had problems even with ext4) rather than NTFS? This could be a problem when trying to move large files from Ubuntu to Windows, because I doubt Windows can read ext4. Or is there a "hamburger helper" allowing Windows to do this easily?

---

### Post by vindju on 2012-10-14
I have the same problem. File is 4.2 Gb , and I get this "file is too large".
My USB disk is formatted ext4. ('bought it yesterday)

---

### Post by engrin on 2012-11-19
Has anyone found a solution to this one yet?

---

### Post by idoitprone on 2012-11-19
nvm

---

### Post by engrin on 2012-11-19
Thanks! 
Is there an application I can download to help with formatting my usb drive?

---

### Post by idoitprone on 2012-11-19
> **engrin said:**
> Thanks! 
Is there an application I can download to help with formatting my usb drive?

gparted

---

### Post by rnerwein on 2012-11-20
> **fayslr said:**
> I am copying a file, which has a size of 4.1 GB from my home folder to my portable usb drive formatted as ext4. When copying operation, reach at 4.0 GB, an error pops "Error splicing file: File too large". I know, that this error usually comes when you copy a file greater than 4 GB on fat32 disks, which has a limit of 4 gigs for the maximum file size, but i have no idea, why this error comes, when an ext4 formatted drive can hold a file upto 16 TB of size.

Can anybody help? I am using Ubuntu 10.04.
i don't know where the problem is when you has formated your usb-stick ext4.
but you can use the command "split - see man split" to get rid of your problem.
just a little question: you ain't manupulated the: /etc/security/limits.conf ???

---

### Post by con.cept.me on 2013-05-02
Have this problem to try to copy a 5 gb file to usb X_x

---

### Post by metroedged on 2014-04-03
I am trying to copy a 5.1gb file onto a 8gb flash drive. I get the same error.

---

### Post by MikeCyber on 2014-08-19
Yes same here while trying to copy 10GB zip to a 100GB NTFS HD.-

---

### Post by dddddttttt2 on 2014-10-15
Before I copy a 4.7G file to a 8G fat32 memory stick, same fail.
Later I format the 8G memory stick with NTFS, I solve the issue.

---

