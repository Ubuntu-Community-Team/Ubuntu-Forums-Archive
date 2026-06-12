---
title: "mounting a dd image"
date: 2010-03-29
forum: General Help
---

### Post by miatawnt2b on 2010-03-29
I have a gziped dd image backup of my entire hda drive (osx and ext4 partitions) that I created with the following command:

 dd if=/dev/sda |gzip > image032810.gz

so the million dollar question is can I mount this image file to pull off individual files from individual partitions?

Thanks,
-J

---

### Post by gmargo on 2010-03-29
Have a look at the **testdisk** package.  It is a "Partition scanner and disk recovery tool".  It can be used with disk image files.

---

### Post by srs5694 on 2010-03-29
The usual way to mount an image file is to use the -o loop option to mount; however, I don't know of any way to mount a *compressed* image file. (There may be such a way and I just don't know about it; it's certainly worth doing some digging if you don't have the disk space to uncompress the file.) If you've got enough disk space to hold an uncompressed image, you could do this:

```

gunzip image032810.gz
sudo mount -o loop image032810 /mnt/whatever

```

Change "/mnt/whatever" to a suitable mount point (empty directory). When you're done, you can recompress the image file, if you like.

---

### Post by gmargo on 2010-03-29
The loopback mount method would work if the image was of one partition (i.e. one filesystem), but it's the whole disk.  I was hoping the OP could use **testdisk** to divide the disk image into partition images.

---

### Post by srs5694 on 2010-03-29
> **gmargo said:**
> The loopback mount method would work if the image was of one partition (i.e. one filesystem), but it's the whole disk.  I was hoping the OP could use **testdisk** to divide the disk image into partition images.

Oops; I missed that. Here's a script that will do the job with whole-disk images, assuming they're partitioned using the Master Boot Record (MBR) or GUID Partition Table (GPT) partitioning systems:

```

#!/bin/bash

# mount_image, a program that mounts a specific partition from a RAW
# disk image file, such as a full-disk dd copy or a file used by QEMU.
# Note that compressed and other space-saving formats (qcaw2, etc.)
# will NOT work!

# Use:
# mount_image image_file partition_number mount_point
#
# For instance,
#
# mount_image image.raw 2 /mnt/shared
#
# mounts partition 2 from image.raw at /mnt/shared.

# This program relies on my GPT fdisk (gdisk) program to help identify
# partitions. I could have used regular fdisk, but this would have
# limited the program to working with MBR-formatted disks. With gdisk,
# both MBR- and GPT-formatted disks will work.

gdisk -l $1 > /tmp/mount_image.tmp
let StartSector=`egrep "^   $2|^  $2" /tmp/mount_image.tmp | fmt -u -s | sed -e 's/^[ \t]*//' | head -1 | cut -d " " -f 2`

let StartByte=($StartSector*512)

echo "Mounting partition $2, which begins at sector $StartSector"

mount -o loop,offset=$StartByte $1 $3

rm /tmp/mount_image.tmp

```

Note that this program relies on [GPT fdisk](http://www.rodsbooks.com/gdisk) to work. To use it:


[list=1]
[*]Install GPT fdisk
[*]Cut-and-paste the preceding script into a file (mount_image, for instance)
[*]Type "chmod a+x mount_image" in a shell prompt in the same directory as the file to make it executable
[*]Copy mount_image to somewhere on your path, such as /usr/local/bin.
[*]Uncompress the image file, as in my earlier post
[*]Type "sudo mount_image 032810 1 /mnt/wherever", changing "1" to the partition number you want to mount and /mnt/wherever to the mount point.
[/list]


This still relies on having sufficient disk space to hold the uncompressed image file.

---

### Post by geirha on 2010-03-29
[http://ubuntuforums.org/showthread.php?t=1000644](http://ubuntuforums.org/showthread.php?t=1000644)

---

### Post by psusi on 2010-03-29
Yes, you can mount it with the loop option if it is unzipped first.  Also you do not want to use dd to make backups like this since it copies unused blocks as well, making for a very large image, and you can not access the contents without decompressing it.

---

