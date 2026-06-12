---
title: "How to mount the partitions on a made image with dd (/dev/sdb) ?"
date: 2010-05-15
forum: General Help
---

### Post by frenchn00b on 2010-05-15
Hello,

my /dev/sdb contains
2 partitions with fat 32
2 partitions with NTFS
1 partition with LINUX ext3
and a swap linux.

I did :
```
dd if=/dev/sdb of=image_disk_sdb.img
```

How can I mount those several partitions please?

---

### Post by dandnsmith on 2010-05-15
I'm not sure you can - the mount command makes provision for mounting filesystems of various types, but you have at least 5 filesystems wrapped up together in one envelope.

Take a look at provision for loop mounting iso filesystem images, and try to work out how the mount command can possibly split the image file into component parts.

HTH

---

### Post by frenchn00b on 2010-05-15
It is possible with 

```
mount -t ext2 -o loop,offset=$((512*509))
```
very complicated

is there a frontend ?

---

### Post by srs5694 on 2010-05-15
Here's a script I wrote that will do the trick; however, this script relies on my [GPT fdisk](http://www.rodsbooks.com/gdisk/) program, so you'll have to install it if you want to use the script. The comments describe the usage.

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

---

### Post by dandnsmith on 2010-05-15
Terrific srs,
That's another new thing for today - the gdisk to get the offset 'automatically'.
I'll have to make a note, just in case.

---

### Post by srs5694 on 2010-05-15
I used gdisk because it produces output that's relatively easy to parse, and it works for both MBR and GPT disks (or disk images). As noted in the script's comment, fdisk could be used instead on MBR disk images (although you'd need to change the details to extract the right data). I'm sure you could get the data from sfdisk, parted, or perhaps other utilities, too. I wrote this as a "quick and dirty" script when I was experimenting with disk images at one point.

---

### Post by jerome1232 on 2010-05-15
I remember when I used to make images of entire drives I would use fdisk to dump the offset's to a file and kept the file with the iso.

I wasn't aware that you could get fdisk or other partition utilities to actually look at the image and get that information. That's pretty nifty actually.

---

### Post by frenchn00b on 2010-05-16
> **srs5694 said:**
> Here's a script I wrote that will do the trick; however, this script relies on my [GPT fdisk](http://www.rodsbooks.com/gdisk/) program, so you'll have to install it if you want to use the script. The comments describe the usage.

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


Thanks a lot very much. Thats a great script that shall go into a script linux database.

---

### Post by honeybear on 2010-12-05
Please find an alternative to the above program:

```

if [ "$1" = "--help" ] ; then
	echo "Busibox help file:"
	echo "arg1 : the file img made with dd"
	echo "arg2 : if --local then mount to somewhere else as /mnt/imgdisk"
	exit
fi

if [ "--local" = "$2" ] ; then 
	echo "Local mount of the $1 file partitions"
	printf "Please enter a location on the disk :>"
	read FOLDERMNT
	echo "Creating $FOLDERMNT ..."
	else
	FOLDERMNT="/mnt/imgdisk"
fi

umount "$FOLDERMNT"
mkdir -p "$FOLDERMNT"

while [ 1 ] ; do 

gdisk -l "$1"

##$1 > /tmp/mount_image.tmp


echo "Partition number :>"
read nbp
echo "Startsector :>" 
read sector


let StartSector=`egrep "^   $nbp|^  $nbp" /tmp/mount_image.tmp | fmt -u -s | sed -e 's/^[ \t]*//' | head -1 | cut -d " " -f 2`
let StartByte=($sector*512)

echo "Mounting partition $nbp, which begins at sector $sector"

mount -o loop,offset=$StartByte "$1" "$FOLDERMNT"
echo "ls:"
ls "$FOLDERMNT"
echo " "
echo "Press Enter to unmount"
read lkdjf
umount "$FOLDERMNT"

done


```

---

