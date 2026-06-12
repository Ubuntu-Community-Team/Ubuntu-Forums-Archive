---
title: "A big mistake!"
date: 2010-05-18
forum: General Help
---

### Post by hirohitosan on 2010-05-18
Hi guys!
I made a huge mistake! During installing FreeBSD on one of my computer I accidentally format (UFS) an USB HDD (fat32) attached to that computer. There are any chances to recover my data?
thanks!

---

### Post by anaconda on 2010-05-18
normal formatting doesn't destroy the data. (well not all of it anyway) 

Photorec is one program, that can search files, when a partition has been destroyed, like in your case. Formatting destroyed partition data, but the files are still there..

---

### Post by hirohitosan on 2010-05-18
Thanks anaconda, I'll try it, hope will work

---

### Post by sedawk on 2010-05-18
In general there are two ways of formatting a disk.
When doing fast format only the management data is
written to the disks and all data blocks are marked
as free but are not initialized themselves (with zeroes).
A slow format might overwrite the whole disk,
"zero" it.

If the disk wasn't "zeroed" there is a chance that you
can recover data that wasn't overwritten by mangement
data by using a "carving" tool.
These tools scan the disk for areas that look like known
structures, e.g. photos.
Have a look at
[http://en.wikipedia.org/wiki/File_carving](http://en.wikipedia.org/wiki/File_carving)

---

