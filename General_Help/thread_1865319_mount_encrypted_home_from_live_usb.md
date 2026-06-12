---
title: "mount encrypted home from live usb"
date: 2011-10-20
forum: General Help
---

### Post by PGScooter on 2011-10-20
Hi,

I am using 11.10 beta 1. I need to mount my encyrpted home from the live usb. I have my password and my passphrase, but I can't figure it out. I've tried to follow several guides on the internet, but I can't get past the mounting step.

Here is my sudo fdisk -l output:

```
12500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a8ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   304373759   152185856   83  Linux
/dev/sda2       304375806   312494079     4059137    5  Extended
/dev/sda5       304375808   312494079     4059136   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a8ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   304373759   152185856   83  Linux
/dev/sdb2       304375806   312494079     4059137    5  Extended
/dev/sdb5       304375808   312494079     4059136   82  Linux swap / Solaris

Disk /dev/mapper/isw_bahfecabg_ARRAY: 160.0 GB, 159997104128 bytes
255 heads, 63 sectors/track, 19451 cylinders, total 312494344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a8ca

                          Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bahfecabg_ARRAY1            2048   304373759   152185856   83  Linux
/dev/mapper/isw_bahfecabg_ARRAY2       304375806   312494079     4059137    5  Extended
/dev/mapper/isw_bahfecabg_ARRAY5       304375808   312494079     4059136   82  Linux swap / Solaris

Disk /dev/mapper/isw_bahfecabg_ARRAY1: 155.8 GB, 155838316544 bytes
255 heads, 63 sectors/track, 18946 cylinders, total 304371712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_bahfecabg_ARRAY1 doesn't contain a valid partition table

Disk /dev/mapper/isw_bahfecabg_ARRAY5: 4156 MB, 4156555264 bytes
255 heads, 63 sectors/track, 505 cylinders, total 8118272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_bahfecabg_ARRAY5 doesn't contain a valid partition table

Disk /dev/sdc: 8019 MB, 8019509248 bytes
251 heads, 44 sectors/track, 1418 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000287b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    15663103     7830528    b  W95 FAT32
ubuntu@ubuntu:/media$ 

```

I cannot mount anything:
```
ubuntu@ubuntu:/media$ sudo mount /dev/sda /media/temp/
mount: unknown filesystem type 'isw_raid_member'
ubuntu@ubuntu:/media$ sudo mount /dev/sda6 /media/temp/
mount: special device /dev/sda6 does not exist

```
why does it say that /dev/sda6 does not exist? I get the same for sdb and sdb6.

Any ideas?

Thanks

---

### Post by bibble235 on 2011-10-20
ubuntu@ubuntu:/media$ sudo mount /dev/sda /media/temp/
mount: unknown filesystem type 'isw_raid_member'

sda is the whole disk you probably want to do 

mount /dev/sda1


ubuntu@ubuntu:/media$ sudo mount /dev/sda6 /media/temp/
mount: special device /dev/sda6 does not exist

You cannot mount sda6 as you only have 1,2 and 5

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1 **           2048   304373759   152185856   83  Linux
**/dev/sda2 **      304375806   312494079     4059137    5  Extended
**/dev/sda5**       304375808   312494079     4059136   82  Linux swap / Solaris

---

### Post by PGScooter on 2011-10-20
> **bibble235 said:**
> ubuntu@ubuntu:/media$ sudo mount /dev/sda /media/temp/
mount: unknown filesystem type 'isw_raid_member'

sda is the whole disk you probably want to do 

mount /dev/sda1


ubuntu@ubuntu:/media$ sudo mount /dev/sda6 /media/temp/
mount: special device /dev/sda6 does not exist

You cannot mount sda6 as you only have 1,2 and 5

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1 **           2048   304373759   152185856   83  Linux
**/dev/sda2 **      304375806   312494079     4059137    5  Extended
**/dev/sda5**       304375808   312494079     4059136   82  Linux swap / Solaris

Thank you for the reply. You are right that /dev/sda6 does not exist, but I think that I also have to mount using -t ecryptfs. However, I'm not sure which one to try this on. I keep getting the following:

```
ubuntu@ubuntu:/media$ sudo mount -t ecryptfs /dev/sdb5 /media/temp/
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=70fa14063eb7d5bf
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : 

```

---

### Post by tlu on 2011-10-20
I can confirm that I wasn't able to access my encrypted home partition from the live CD under Kubuntu 11.10 using the method described in [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) although it had worked in 11.04. 

Something has changed in 11.10. I guess the culprit is that /dev/shm now points to /run/shm.

---

### Post by PGScooter on 2011-10-20
thanks, tlu, confirmation is always nice! It means I'm not crazy :)

Did you try to do it using 11.10 beta or the final version?

---

### Post by tlu on 2011-10-21
> **PGScooter said:**
> thanks, tlu, confirmation is always nice! It means I'm not crazy :)

Did you try to do it using 11.10 beta or the final version?

I'm using the final version.

Someone in another forum suggested to create /dev/shm and to add

```
none	/dev/shm	tmpfs	defaults	0	0
```

to /etc/fstab to make it work again. I haven't tried that yet, though.

---

### Post by PGScooter on 2011-10-21
> **tlu said:**
> I'm using the final version.

Someone in another forum suggested to create /dev/shm and to add

```
none	/dev/shm	tmpfs	defaults	0	0
```

to /etc/fstab to make it work again. I haven't tried that yet, though.

ok, thanks for the suggestion. I don't know if I'll try that, but if I figure out a solution, I'll post back here.

---

