---
title: "Backup system with file comparisons?"
date: 2006-06-16
forum: General Help
---

### Post by Boelcke on 2006-06-16
One useful application I miss from Windoze is Syncback.  It's a backup app that has a bunch of nifty features, including writing to an ftp site.  It has the usual bells and whistles, such as automatically running periodically, etc.

The most useful thing about it for me, which most other backup systems don't seem to have, is the ability to CHECK the files it's backing up, compared to the backup.  One of my primary piles of data that I backup is a large repository of digital photos and videos.  When I had Syncback set to back these up, it did more than just copy the directory over.

If the files did not exist in the backup, it could prompt me.
If the files did not exist in the sources, it could prompt me.
**It would check the md5 checksums, and if one of the files was not like the other, it would prompt me.**

I can't seem to find this checksum option in a linux-based app.  Most backup systems, when faced with a newer version in the source, will UPDATE the copy in the backup.  They're just generally built with the attitude that the latest and greatest must be the best.  If the file has been corrupted, it then backs up the corrupted file, writing over my good backup!

Short of learning how to write scripts (I can see that I'll need to do that at some point), can you suggest an application I can run under ubuntu to do all this?

---

