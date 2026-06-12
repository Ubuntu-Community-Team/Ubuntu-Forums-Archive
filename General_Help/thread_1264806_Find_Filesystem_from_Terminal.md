---
title: "Find Filesystem from Terminal"
date: 2009-09-12
forum: General Help
---

### Post by nmaster on 2009-09-12
Suppose I mount an external hard drive.  From the command line, how do I find the type of file system?  

I noticed that "sudo fdisk -l" disagrees with "Properties" (from GUI). As documented here: [http://ubuntuforums.org/showthread.php?t=1244318](http://ubuntuforums.org/showthread.php?t=1244318)

---

### Post by niteshifter on 2009-09-12
Hi,

The file command:

```
sudo file -s /dev/sdXY
```
where X is a, b, c, etc. and Y is 1, 2, 3, etc.

---

### Post by P4man on 2009-09-12
it says filesystem '**fuseblk**" for your mountpoint. Im going out on a limb here, but I think you are mounting that drive in fstab with incorrect settings? Using ntfs-3G driver to mount a FAT volume. Or something :)

---

### Post by unutbu on 2009-09-12
The filetype of mounted filesystems is reported by 
```

df -T
```
or ```

mount
```

---

### Post by unutbu on 2009-09-12
neal.m.master, the partition has a type, and the filesystem has a type. The filesystem sits inside of the partition -- they are not the same thing.

"sudo fdisk -l" reports the partition type
"df -T" or "mount" or the "Properties" GUI reports the filesystem type.

mount reports "fuseblk"  when a filesystem is NTFS. So I think /media/disk is an NTFS filesystem, perhaps inside a W95 FAT32 partition.

There is nothing terribly wrong with that as far as Linux is concerned. Linux ignores the partition type. 

If you wish, you can change the partition type of /dev/sdc1 to HPFS/NTFS
with this command
```

sudo sfdisk --change-id /dev/sdc 1 7
```

This command is non-destructive. It will not harm your data.

---

### Post by nmaster on 2009-09-14
> **unutbu said:**
> neal.m.master, the partition has a type, and the filesystem has a type. The filesystem sits inside of the partition -- they are not the same thing.

"sudo fdisk -l" reports the partition type
"df -T" or "mount" or the "Properties" GUI reports the filesystem type.

mount reports "fuseblk"  when a filesystem is NTFS. So I think /media/disk is an NTFS filesystem, perhaps inside a W95 FAT32 partition.

There is nothing terribly wrong with that as far as Linux is concerned. Linux ignores the partition type. 

If you wish, you can change the partition type of /dev/sdc1 to HPFS/NTFS
with this command
```

sudo sfdisk --change-id /dev/sdc 1 7
```This command is non-destructive. It will not harm your data.



Aha!! This explains the issue.  I also didn't know that "fuseblk" = "NTFS" in the return of mount.  The command worked like a charm, but could you explain how you knew that "7" was the necessary id?  I skimmed through the man page and understand everything else.

Thanks all.

---

### Post by unutbu on 2009-09-14
neal.m.master, I'm glad this helped.
If you type
```

sfdisk -T
```

sfdisk will list all the partition types. There you can find the number corresponding to "HPFS/NTFS".

---

