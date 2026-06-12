---
title: "fstab is messed up"
date: 2012-08-22
forum: General Help
---

### Post by bobman321123 on 2012-08-22
I edited my fstab to allow for mounting a partition as part of the file system.
Since then, I've juggled the partitions around to make room for windows again, and I'd like it if someone could tell me how to restore my fstab back to the default.
Thanks

---

### Post by drmrgd on 2012-08-22
I'm not sure there's really such a thing as a 'default' fstab as such.  However, if you post the results of:

```
cat /etc/fstab
```

and 

```
sudo blkid
```

I think that will give us an idea of what your current partitioning scheme is and how it should be set up in fstab.

---

### Post by bobman321123 on 2012-08-27
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=240553a1-a638-4c00-b4d4-01ee9b235d9a   /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=e7cbcac5-9e26-4654-ae6f-6f7b228d6466 none swap sw 0 0
/dev/mapper/cryptswap1                      none         swap  sw                   0  0  
/dev/mapper/cryptswap2                      none         swap  sw                   0  0  
/dev/mapper/cryptswap3                      none         swap  sw                   0  0  
UUID=44EBC5660C2616FA /mnt/data ext4 auto,users,rw,relatime 0 2

```

```
/dev/sda1: UUID="2A0839BF08398B39" TYPE="ntfs" 
/dev/sda2: UUID="44EBC5660C2616FA" TYPE="ntfs" 
/dev/sda5: UUID="240553a1-a638-4c00-b4d4-01ee9b235d9a" TYPE="ext4" 
/dev/sda7: UUID="3A9E3E5E31D6AD88" TYPE="ntfs" 
/dev/mapper/cryptswap2: UUID="bfd2efe7-65f4-4541-b1ff-a2c2e667ad8b" TYPE="swap" 
```

---

### Post by oldfred on 2012-08-27
My suggestions. You changed data partition from ext4 to ntfs and have only one swap with an encrypted /home so all the other swaps are commented out. If it works ok, then you can delete the commented out lines.

sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

 If you are in system or can boot run this after changes. If mounting from liveCD path will include the /media and mount that you give it.
sudo mount -a
If no errors it just returns or else tells you the issue.

```

# /etc/fstab: static file system information.
#

# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=240553a1-a638-4c00-b4d4-01ee9b235d9a   /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
[COLOR=Red]#[/COLOR]UUID=e7cbcac5-9e26-4654-ae6f-6f7b228d6466 none swap sw 0 0
[COLOR=Red]#[/COLOR]/dev/mapper/cryptswap1                      none         swap  sw                   0  0  
/dev/mapper/cryptswap2                      none         swap  sw                   0  0  
[COLOR=Red]#[/COLOR]/dev/mapper/cryptswap3                      none         swap  sw                   0  0  
UUID=44EBC5660C2616FA /mnt/data [COLOR=Red]ntfs [/COLOR]auto,users,rw,relatime 0 [COLOR=Red]0[/COLOR]

```Preferred entry style:
For ntfs:
```
UUID=44EBC5660C2616FA /mnt/data ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

```

---

### Post by bobman321123 on 2012-08-28
Thanks oldfred, that worked perfectly. :)

---

### Post by oldfred on 2012-08-28
Glad that worked. :)

---

