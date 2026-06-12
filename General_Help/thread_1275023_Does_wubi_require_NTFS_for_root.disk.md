---
title: "Does wubi require NTFS for root.disk?"
date: 2009-09-25
forum: General Help
---

### Post by drsquirrel on 2009-09-25
At first I was having issues with "Bad File Descriptor" and a log on my c: filling the drive (trying to install wubi on another drive at this point).

The drive is FAT32, and I assume root.disk is trying to be 11gb (the install size) and thus cannot sit on FAT32.

Does Wubi really need NTFS, or is there a way around to use FAT32?


Before I started this post I was going to ask about the error, but I eventually opened the log file using command line "edit"... nothing else would open it (notepad, wordpad, notepad++). And found out the above, ive also searched on that... and the solution that people tend to give is... reformat to ntfs, and that really isn't a solution for me.


Or, Is there a way to use multiple partitions using Wubi (4gb root, 4gb home, 4gb app etc)?

---

