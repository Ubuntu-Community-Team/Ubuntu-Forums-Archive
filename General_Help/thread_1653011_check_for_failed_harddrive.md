---
title: "check for failed harddrive?"
date: 2010-12-26
forum: General Help
---

### Post by supermooshman on 2010-12-26
Hi all,

recently I installed xubuntu on my eee, and after a few uses my secondary harddrive disappeared.
I tried adding it to fstab using and mounting it through the terminal
which gives my the following output:```
~$ sudo mount /dev/sdb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```

somewhere on the forum I found a link [http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
using e2fsck I got following output
```
~$ sudo e2fsck -f /dev/sdb
e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

using an alternate superblock (8193) gives the exact same output


Anyone any idea what I can try next?




oh and happy Kwanzaa :)

---

### Post by oxfms on 2010-12-26
Maybe 

```
sudo mount /dev/sdbn
```where n is the desired partition you'd like to mount. Same for e2fsck.

---

### Post by mcduck on 2010-12-26
You are trying to mount a drive, not a partition. That's not going to work. ;)

Also, if the filesystem you are trying to mount isn't defined in /etc/fstab, you need to at least specify a mount point in the mount command. (You might need to tell the file system as well)

Assuming it's the only partition on the drive:

```
sudo mount /dev/sda1 /mnt
```

---

### Post by supermooshman on 2010-12-26
> **oxfms said:**
> Maybe 

```
sudo mount /dev/sdbn
```where n is the desired partition you'd like to mount. Same for e2fsck.
same thing happened as before

> **mcduck said:**
> You are trying to mount a drive, not a partition. That's not going to work. ;)

Also, if the filesystem you are trying to mount isn't defined in /etc/fstab, you need to at least specify a mount point in the mount command. (You might need to tell the file system as well)

Assuming it's the only partition on the drive:

```
sudo mount /dev/sda1 /mnt
```

it did mount, but how to access it (God i feel stupid)
ls just gives me:```
ls -a /mnt
. .. lost+found
```

---

### Post by mcduck on 2010-12-26
Well, try "sdb1" instead of "sda1". Anyway, the point is that you must specify the correct disc *and* correct partition to mount. You can't mount a disc ("sda" or "sdb"), you mount a filesystem. Which will always be located on a certain partition ("sdb1", "sda5" or something like that).

Seems like you are already accessing it. Or *some* mounted partiton, at least... Although the only directory on the drive is lost+found, which is a place where fsck stores broken files.

---

### Post by supermooshman on 2010-12-26
> **mcduck said:**
> Well, try "sdb1" instead of "sda1".

my bad, I actually did mount sdb1 instead of sda1 (god damn you copypaste!)
anyway, I get no output, and ls -a just gives me the list above

any further ideas?
thanks

---

### Post by mcduck on 2010-12-26
> **supermooshman said:**
> my bad, I actually did mount sdb1 instead of sda1 (god damn you copypaste!)
anyway, I get no output, and ls -a just gives me the list above

any further ideas?
thanks

well, in that case it looks like you've had some filesystem related problem on the drive, and fsck has recovered what it can into the lost+found directory on the drive.

Try looking there and you might still be able to save some of your files. And then check the SMART status of the drive, and also the system logs for any I/O errors on the drive, it might be failing....

---

