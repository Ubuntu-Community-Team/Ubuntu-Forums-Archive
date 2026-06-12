---
title: "looking for partition analysis utility"
date: 2010-08-11
forum: General Help
---

### Post by dwalby on 2010-08-11
Is anyone aware of a utility that can show all the files in a partition and their sector locations? This would seem like something that file recovery software would have to be able to figure out in the process of recovering deleted files, but not sure if any utility would actually display the information in that manner. Before anyone asks, I don't think I really NEED to know that information, but I'm just curious to see how the sectors are allocated as the partition fills up and files are created and deleted. Prior to resizing a partition smaller it would be interesting to see if data has to be moved from the end of the partition because it occupies sectors that will be lost due to the resizing operation.

---

### Post by dwalby on 2010-08-13
Found a utility called nfi.exe that works with NTFS partitions.  Ran it on each of my NTFS partitions and then Perl scripted the result to show what's in each partition sorted by either incremental sector indexes or alphabetized filenames.  It also shows which files are fragmented as they show up with multiple sector ranges.

---

