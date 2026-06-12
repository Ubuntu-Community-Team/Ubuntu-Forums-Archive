---
title: "recovering corrupt JPEG files from CD"
date: 2010-05-16
forum: General Help
---

### Post by Hulabear263 on 2010-05-16
During a trip to Hawaii in July of 2006 I had my first digital camera.  Once the storage
cards were full I went to an Internet Cafe in Hilo to copy the images to CD so that I
could take more photos.  I was careful about matching the files and byte counts on the
CD and the original hard drive folder containing the camera data before erasing the
source files.  I was able to view the copied images on the CD without any problem on
the computer that I used to create the CD.  However, upon my return home I found
that many of the copied images could not be viewed or accessed.  Tried to use a
program called ISOBUSTER to get at the files, but no joy.  Also attempted to get the
photos using some other software (don't recall which at this point; it's been a while),
but still no luck.  Did get some images, but they looked scrambled, like a jigsaw puzzle
put together wrong:  rectangular strips transposed into wrong places in the frame.
Tried using the right-click Check Disc function that came with Lucid Lynx, but get this
message:  The file integrity check could not be performed.  No checksum file could
be found on the disc.   Any ideas on how to fix these CDs and files?  I can't even
copy the entire CD, just those files that are uncorrupted.  Thanks!

---

### Post by frostschutz on 2010-05-16
make an image of the disk, leaving out unreadable sectors

dd if=/dev/cdrom of=cdrom.iso conv=noerror,sync

then loop-mount it

mount -o loop cdrom.iso /mnt/cdrom

then see if the files on there are usable at all
if the mount fails, use testdisk / photorec on the cdrom.iso

also if the cd image you get has errors, try cleaning the disk (if it has dirt / scratches), also try reading it in several different drives several times, some drives cope with bad disks better than others-

if you still have the storage cards, and the storage cards haven't been (fully) written on with new images, use photorec on the storage cards as well

---

