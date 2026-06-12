---
title: "Can't Access Filesystem"
date: 2010-02-11
forum: General Help
---

### Post by alexrdavies on 2010-02-11
I have an Acer Aspire One Netbook running Ubuntu Netbook Remix 9.10.  Previously it worked fine.  Now when I try to boot it, it displays

[I]GRUB loading.
error: unknown filesystem
grub rescue>
[/I]
It will happily boot a Live USB so it's still usable - but I want to get my data off it.  So far I have been unable to mount the drive, but I am still a novice at using the command line, so I may just be making a mistake.

Here is some of the output from the Terminal running off a Ubuntu Netbook Remix 9.10 Live USB stick:

*ubuntu@ubuntu:~$ *sudo fdisk -l[I]

Disk /dev/sda: 8069MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029344

   Device Boot     Start       End     Blocks   Id  System
/dev/sda1   *         1    7486258+  83  Linux
/dev/sda2          933     393592+   5  Extended
/dev/sda5          933     393561    82  Linux Swap / Solaris

[/I][I]Disk /dev/sdb: 4023MB, 4023385600 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
  
   Device Boot     Start       End     Blocks   Id  System
/dev/sdb1   *         1         488  3919841    b  W95 FAT32
[/I]
*ubuntu@ubuntu:~$* sudo mkdir /wheretomount
*ubuntu@ubuntu:~$ *sudo mount /dev/sda1 /wheretomount[I]
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
   missing codepage or helper program, or other error
   In some cases useful info is found in syslog - try
   dmesg ¦ tail or so

ubuntu@ubuntu:~$ 
[/I]
So, any tips on what I can do?

EDIT: sudo mount -t vfat /dev/sda1 /wheretomount gives the same response.
sudo mount -t ntfs /dev/sda1 /wheretomount gives 
[I]NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used?  Or the whole disk instead of a partition?  Or the other way around?
[/I]

---

### Post by ironclaw on 2010-02-11
You can run "dmesg | tail" as it suggests after "sudo mount /dev/sda1 /wheretomount" to see the last system messages. That may be useful.

Also, shouldn't the file system be something like ext4 or ext3 instead of vfat and ntfs? fdisk gives the system ID as 'Linux', so shouldn't contain vfat or ntfs if it was previously formatted with a tool like gparted.

---

### Post by synapsys on 2010-02-11
Since sda is linux and sdb is fat32, don't you want to use:

```
sudo mount -t vfat /dev/sd**b**1 /wheretomount
```

---

### Post by ironclaw on 2010-02-11
I think alexrdavies is running the live USB off /dev/sdb.

---

### Post by alexrdavies on 2010-02-12
Thanks for the replies!

**@ironclaw**, I've just tried
sudo mount -t ext4 /dev/sda1 /whereto mount
& sudo mount -t ext3 /dev/sda1 /whereto mount
& sudo mount -t ext2 /dev/sda1 /whereto mount.

All of them returned
[I]mount: wrong fs type, bad option, bad superblock on /dev/sda1,
   missing codepage or helper program, or other error
   In some cases useful info is found in syslog - try
   dmesg ¦ tail or so[/I].

As for dmesg, that returns a lot of stuff that I don't really understand, but here's what was written at the bottom which looks sort of relevant:

[136.103042] EXT4-fs (sda1): ext4_check_descriptors: Block bitmap for group 0 not in group (block 65569152)!
[136.103069] EXT4-fs (sda1): group descriptors corrupted!
[151.385459] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[248.978398] EXT2-fs: sda1: couldn't mount because of unsupported  optional features (244).
[348.101348] EXT4-fs (sda1): ext4_check_descriptors: Block bitmap for  group 0 not in group (block 65569152)!
[348.101376] EXT4-fs (sda1): group descriptors corrupted!

**@synapsys**, I'll admit I'm not 100% sure, but based on the file sizes I think sda is the hard drive and sdb is the USB stick.  I left it in for completeness.

---

### Post by ironclaw on 2010-02-12
Hmm... It looks like an ext4 file system that somehow got corrupted. Try running
```
sudo fsck.ext4 -p /dev/sda1
```
to see if the problem can be automatically fixed.

If your data is very important, I would suggest using dd to backup the entire drive before doing anything.

---

### Post by alexrdavies on 2010-02-12
Hey, that's pretty much worked!

There's still a lot of stuff it wouldn't rescue, so the system won't boot up, but I can mount the drive now and all my important files are intact.  Thanks a lot for your help.

**Problem solved!**

---

