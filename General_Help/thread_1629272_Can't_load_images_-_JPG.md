---
title: "Can't load images - JPG"
date: 2010-11-23
forum: General Help
---

### Post by alexmfm on 2010-11-23
hi,

i'm having a problem opening photos taken with a nikon coolpix l10.
inserting the memory card and opening a random photo generates an error : 
"Could not load image 'xxx.JPG'."
"Error interpreting JPEG image file (JPEG datastream contains no image)"

opening via terminal with gthumb gives the same error inumerous times : 

"Error: Directory Nikon1 with 1000 entries considered invalid; not read.
Error: Upper boundary of data for directory Photo, entry 0x0000 is out of bounds: Offset = 0x00000001, size = 238602, exceeds buffer size by 195079 Bytes; adjusting the size
Warning: Directory Photo, entry 0x0000 has unknown Exif (TIFF) type 0; setting type size 1.
Error: Directory Thumbnail: Next pointer is out of bounds; ignored."

i tried renaming one of the pics to xxx.JPEG but still no luck (no thumbnail is shown either).
it happens with all photos taken with this camera and i can open these photos in other pc's.
can someone reproduce the same error?
any ideas on how to solve this?

Update : 

aparently, conecting the camera directly to ubuntu (via usb cable) instead of removing the memory card and mounting it solves the problem.
it seems it is a behaviour consistent to other nikon cameras. jpeg has a different compression or some kind of filesystem protection maybe?
anyway, issue solved.

---

