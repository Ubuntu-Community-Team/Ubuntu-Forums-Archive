---
title: "Unable to mount /dev/sda1 - can't find volume"
date: 2010-08-21
forum: General Help
---

### Post by lowkey_246 on 2010-08-21
The problem I'm having didn't seem to be covered in other posts.   Despite following what is supposed to be a straigtforward method, I am  still unable to mount /dev/sda1.

Using Ubuntu 10.04 LTS LiveCD -  Lucid Lynx

sudo /bin/bash
fdisk -l
[INDENT]Disk  /dev/sda: 250.1 GB
Disk identifier: 0xa08ea08e

   Device     Boot          Start          End           Blocks    Id   System
/dev/sda1       *                1       22309     179197011    7    HPFS/NTFS
/dev/sda2                  22310       30401      64998990    7    HPFS/NTFS
[/INDENT]mkdir  /mnt/winblows
mount -t ntfs-3g /dev/sda1 /mnt/winblows -o force
[INDENT]ntfs-3g:  Failed to access volume '/dev/sda1': No such file or directory

blah  blah blah....
[/INDENT]I find it strange that fdisk sees the  drive but mount doesn't.  Anyone know what might be causing this?   Thanks in advance for your help.

---

### Post by deserthowler on 2010-08-21
> **lowkey_246 said:**
> 


mount -t ntfs-3g /dev/sda1 /mnt/winblows -o force



Do your mount as sudo.

Earl

---

### Post by lowkey_246 on 2010-08-22
nope, still get the same error.  i've tried adding sudo before each command and it doesn't make a difference.

---

