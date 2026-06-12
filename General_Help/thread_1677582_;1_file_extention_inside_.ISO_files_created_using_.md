---
title: ";1 file extention inside .ISO files created using &quot;dd&quot;"
date: 2011-01-28
forum: General Help
---

### Post by SlimBiggins on 2011-01-28
I am in the process of backing up a bunch of CDs. I have been using the following command to do so:

```
dd if=/dev/cdrom of=/media/sdb/filename.iso
```I've noticed that in most of the .ISO images created this way (nearly all), when mounted using Archive Mounter or when viewed using Archive Manager, every file has **;1** at the end of the filename after the appropriate file extension.

1. What is the purpose of this **;1** extension?
2. Is there an argument I can use to stop **dd** from creating this extension?
3. And is **dd** the best for backing up CDs to an image file? (As far as reliability goes)

The problem is that I'm mounting the .ISO images as a virtual drive (instead of burning a copy of every disk I use), but the **;1** at the end of every file doesn't allow the files to be opened/executed with a double-click because nautilus does not recognize the type of file.

Any help is always greatly appreciated =)
- SlimBiggins

---

### Post by mrhhug on 2011-01-28
i would definetly not use dd, doesnt that take forever?

try some of these [http://tuxarena.blogspot.com/2009/03/4-ways-to-create-cddvd-iso-images-in.html](http://tuxarena.blogspot.com/2009/03/4-ways-to-create-cddvd-iso-images-in.html)

or you can try

```
cat /dev/scd0 > /home/yourname/test.iso
```

---

### Post by srs5694 on 2011-01-29
> **SlimBiggins said:**
> I am in the process of backing up a bunch of CDs. I have been using the following command to do so:

```
dd if=/dev/cdrom of=/media/sdb/filename.iso
```I've noticed that in most of the .ISO images created this way (nearly all), when mounted using Archive Mounter or when viewed using Archive Manager, every file has **;1** at the end of the filename after the appropriate file extension.

1. What is the purpose of this **;1** extension?
2. Is there an argument I can use to stop **dd** from creating this extension?

I'm not familiar with Archive Mounter or Archive Manager, so I can't speak to what they're doing; however, the dd command you presented does not change the data you're copying. The ;1 extension is a file version number, which is an optional part of the ISO-9660 standard. See [this wiki page,](http://www.gearsoftware.com/wiki/index.php?title=ISO9660_-_File_and_directory_names) for instance; or search on "iso-9660 semicolon" for more information. 

Linux ordinarily hides this file version number. You can change mount options to display them, though:

```

sudo mount -o map=off,norock,nojoliet /dev/sr0 /mnt

```

Change the device filename (/dev/sr0) and mount point (/mnt) as necessary or desired. Note that to display these version numbers, you must also ignore the Rock Ridge and Joliet extensions, which provide long filenames that do not include the version number. Thus, the filenames may not exactly match what you normally see, beyond the version number.

> 3. And is **dd** the best for backing up CDs to an image file? (As far as reliability goes)

Assuming the original disc is readable, yes, dd will work fine. Mrhhug's concern about dd's speed isn't an issue for typical data CDs. The speed problem with dd only applies to hard disk partitions, which typically contain large chunks of unused disk space that dd will nonetheless dutifully copy, wasting time. Data CDs normally lack such big unused spaces, so you needn't be concerned with this issue when copying data CDs.

If the disc has errors on it, then you'd be better off using ddrescue or gddrescue (both are in the Ubuntu repositories). The dd program aborts when it encounters an error, resulting in a short file. The ddrescue program doesn't do this; instead, it leaves a gap in the file, which is likely to corrupt one file and leave the rest of the disc intact. The gddrescue program makes repeated attempts to read bad sectors, which is more likely to recover data even from damaged discs.

> The problem is that I'm mounting the .ISO images as a virtual drive (instead of burning a copy of every disk I use), but the **;1** at the end of every file doesn't allow the files to be opened/executed with a double-click because nautilus does not recognize the type of file.

Try this:

```

sudo mount -o loop -t iso9660 imagefile.iso /mnt

```

Change imagefile.iso to your image file's filename and /mnt to your desired mount point. For some discs (particularly some DVDs), you may need to change iso9660 to something else -- typically udf, but sometimes hfs or hfsplus for discs that originated on Macs. This command should mount the image without displaying the ISO-9660 version number, just as if you'd mounted the disc normally. It sounds like the Archive Mounter program you're using does things strangely.

---

### Post by New Reply on 2012-04-25
Old thread, but it comes up in Google when searching this subject...

I struggled with this issue.  The mount options for iso9660 are rather annoying.  Linux by default converts filenames to lowercase.  You can turn this off with the map=off option, but this also turns on the ;1 version numbers.  I solved the issue as follows...

1. mount iso image somewhere eg:
mount -o loop image.iso /mnt

2. make a new image, using genisoimage -N flag (which omits version numbers):
genisoimage -N -o new.iso /mnt

3. umount old iso
umount /mnt

4. mount new iso with map=off:
mount -o loop,map=off new.iso /mnt

YMMV

---

### Post by tijs14tijs on 2012-07-12
Hey guys, i made a script for this. 
just execute it and paste the wrong iso file to it. it will convert it to a properly file-named iso.
Thanks for your information New Reply!

WARNING: THERE IS NO SUPPORT FOR SPACES IN THE PATH!

```

#!/bin/bash
# Name: fixISOFileNames.sh
# Author: Tijs Maas
# [You are free to modify and redistribute this] 
# License: GPLv3
# Last updated: 12/08/2012 (DD/MM/JJJJ)
# Script solve filename problems(file.txt;1) in ISO Decoding 
# WARNING: THERE IS NO SUPPORT FOR SPACES IN THE PATH!

args=("$@")
FILE=${args[0]}
DIR="/mnt/"
FULLFILENAME=${FILE##*/}

if [ $# -ne 1 ]; then
	echo "Type -h if you need instructions"
	exit 1
fi

if [ ${FILE} = "-h" ]; then
	echo 'Usage: ./fixISOFileNames.sh [filename]';
	echo 'IMPORTANT: You need to be root!';
	echo 'WARNING: THERE IS NO SUPPORT FOR SPACES IN THE PATH!';
	exit 0
fi

CURRENTDIR="$(dirname ${args[0]})"
NEWFILENAME=${FULLFILENAME%.*}"_fixed.iso"
NEWDIRFILE=${CURRENTDIR}"/${NEWFILENAME}"
LOGFILE='fixISOFileNames.log'

if [ "$(id -u)" != "0" ]; then
	echo "You must be root to execute this!"
	exit 1
fi

echo "LOG START: fixISOFileNames executed:" > ${LOGFILE}

if [ "$(ls -A $DIR)" ]; then
	umount ${DIR} > ${LOGFILE}
fi

if [ -e $FILE ] && [ ! "$(ls -A $DIR)" ]; then
	echo "new fixed iso will be created: " ${NEWDIRFILE}
	sudo mount -o loop ${FILE} ${DIR} > ${LOGFILE}
	echo 'Generating new iso (this could take a while)'
	genisoimage -N -quiet -log-file ${LOGFILE} -o ${NEWDIRFILE} ${DIR}
	CODE=$?

	umount ${DIR} > ${LOGFILE}
	sudo mount -o loop,map=off ${NEWDIRFILE} ${DIR} > ${LOGFILE}
	sudo umount ${DIR} > ${LOGFILE}

	sudo chgrp users ${NEWDIRFILE} > ${LOGFILE}
	sudo chmod 777 ${NEWDIRFILE} > ${LOGFILE}

	sudo chgrp users ${LOGFILE} > ${LOGFILE}
	sudo chmod 777 ${LOGFILE} > ${LOGFILE}
	
	if [ $CODE = 0 ]; then
		echo "success"
	else
		echo "genisoimage failed!"
		echo "check the log for details: "${LOGFILE}
		exit 3
	fi
else 
	echo "File does not exist"
	echo "Type -h or --help if you need instructions"
	exit 2
fi

```

WARNING: THERE IS NO SUPPORT FOR SPACES IN THE PATH!
Hope you still like my sucky script :lolflag:

---

