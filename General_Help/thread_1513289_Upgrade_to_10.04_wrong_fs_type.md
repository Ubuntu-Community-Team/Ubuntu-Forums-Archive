---
title: "Upgrade to 10.04 wrong fs type"
date: 2010-06-19
forum: General Help
---

### Post by mwjones on 2010-06-19
Just upgraded from 9.10 to 10.04 and cannot mount one of my partitions.  It is encrypted/decrypted in the following fashion:

```
# dd if=/dev/random bs=4k count=1 | gpg -a --cipher-algo AES256 -c - > /mnt/usb/keys/fs.gpg
# gpg -q -o - /mnt/usb/keys/fs.gpg | cryptsetup -v -h sha512 -c aes-xts-plain -s 512 create crypto /dev/md1
# mkfs.ext4 /dev/mapper/crypto 
# mount /dev/mapper/crypto /crypto
```

It has been this way for a long time, survived several release upgrades.  Now when I decrypt it, I have to use gpg in one command to decrypt the key to a file, then use cat in a second command to pipe to cryptsetup, as such:

```
# gpg -q /mnt/usb/keys/fs.gpg
# cat /mnt/usb/keys/fs | cryptsetup -v -h sha512 -c aes-xts-plain -s 512 create crypto /dev/md1
```

Ok a pain, but no big deal.  However, I can no longer mount the device:

```
# mount /dev/mapper/crypto /store/
mount: you must specify the filesystem type
```

This is how it's always been mounted.  Well I know it's ext4, so I supplied that and was greeted with:

```
# mount -t ext4 /dev/mapper/crypto /store/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/crypto,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The only item in dmesg is:

```
[   78.212761] EXT4-fs (dm-0): VFS: Can't find ext4 filesystem
```

What's the deal?  How do I fix this?

---

### Post by mwjones on 2010-06-19
I have a netbook running 8.10 and an external hdd that is used for backup and encrypted/decrypted in the same manner. Plugging the external hdd into the netbook, the normal decryption process on the external hdd worked fine. So to me that indicates that something changed in 10.04 causing this to be an issue, as there were no issues with 8.10 and 9.10.

How can I narrow down the root cause?

---

### Post by mwjones on 2010-06-21
I decided to wipe the drives and restore from backups.  This time, though, I used the -d option in cryptsetup.  FML.

---

### Post by ilon_s on 2010-09-02
*bump*

Got almost the same problem.

After upgrade to 10.04 from 9.10 i can no longer mount my partition.

Unlocking works just fine with:

```
root@Starshine:/# cryptsetup --verbose luksOpen /dev/mapper/group1-media media
Enter passphrase for /dev/mapper/group1-media: 
Key slot 0 unlocked.
Command successful.
```

But then when i try to mount it i get an error about wrong fs, and setting the fs manually dosnt work either.

```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/media,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I have a few drives in a LVM-configuration with luks ontop, worked just fine untill the upgrade.

cfdisk -l of the unlocket device gives me:
```
Disk /dev/mapper/media: 1160.1 GB, 1160059547648 bytes
255 heads, 63 sectors/track, 141035 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf960c21c

Disk /dev/mapper/media doesn't contain a valid partition table
```

Any suggestions are welcome, tried this from a 9.10-livecd aswell, just to make sure, same problems / output.

This is one of two drives, setup identically that got this error after upgrading, and the chance both fails at the same time feels very small.

---

