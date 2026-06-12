---
title: "Scalpel help"
date: 2011-07-04
forum: General Help
---

### Post by cadogan32 on 2011-07-04
I ran the program Scapel to try to recover some pictures from a memory card.It finished but i can't find the pictures in the output directory,on my desktop.All it has in there is a audit.txt file 3 jpg documents and 2 mov documents.they all look like text files though but i can't open them.Here is the output when i ran the file:

sudo scalpel /dev/sdc -o output
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.

Opening target "/dev/sdc"

Image file pass 1/2.
/dev/sdc: 100.0% |**************************************|    1.9 GB    00:00 ETAAllocating work queues...
Work queues allocation complete. Building carve lists...
Carve lists built.  Workload:
jpg with header "\xff\xd8\xff\xe0\x00\x10" and footer "\xff\xd9" --> 2072 files
AVI with header "\x61\x6e\x64" and footer "\x44\x69\x56\x58\x2f\x4d\x50\x45\x47\x2d\x34" --> 0 files
avi with header "\x52\x49\x46\x46\x3f\x3f\x3f\x3f\x41\x56\x49" and footer "" --> 0 files
mov with header "\x3f\x3f\x3f\x3f\x6d\x6f\x6f\x76" and footer "" --> 11 files
mov with header "\x3f\x3f\x3f\x3f\x6d\x64\x61\x74" and footer "" --> 10 files
mov with header "\x3f\x3f\x3f\x3f\x77\x69\x64\x65\x76" and footer "" --> 0 files
Carving files from image.
Image file pass 2/2.
/dev/sdc: 100.0% |**************************************|    1.9 GB    00:00 ETAProcessing of image file complete. Cleaning up...
Done.
Scalpel is done, files carved = 2093, elapsed = 2675 seconds.

not sure where they disappeared too but somewhere there should be 2093 of them :p Any idea where they might be?thanks

---

### Post by cadogan32 on 2011-07-04
nevermind,i just didnt have root permission to access it.:) please delete this message.

---

