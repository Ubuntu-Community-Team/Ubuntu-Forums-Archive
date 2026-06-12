---
title: "rsync - filesystem time differences cause unnecessary uploads"
date: 2009-10-09
forum: General Help
---

### Post by StuartN on 2009-10-09
I have data sets on different computers using different file systems and, most of the time, rsync does exactly what I want it to do.

However I have one a large collection on an NTFS filesystem that I am synchronising with a share on an XFS filesystem. The first upload was fine, but every subsequent synchronisation unnecessarily uploads a large number of unchanged files. Changes on the NTFS master copy are usually in the form of new files, but occasionally there is an edit.

The reason for rsync copying unchanged files is because there are minute differences in the date and time represented on the two filesystems, so that sometimes the converted time on the XFS filesystem is "older" than the original representation on NTFS. So the odd microsecond conversion error is hours of duplicated uploads.

Is there any more elegant solution than ignoring the timestamp altogether using --size-only, which might miss a real edit that does not alter file sizes?

---

### Post by alphaniner on 2009-10-09
There is an option to compare files by checksum rather than timestamp, but it can be very time consuming.

```
-c, --checksum              skip based on checksum, not mod-time & size
```

---

### Post by StuartN on 2009-10-09
> **alphaniner said:**
> There is an option to compare files by checksum

Excellent - I can do regular --size-only synchronisations and then a checksum synchronisation after major editing sessions.

I suppose if I nuke the NTFS stuff around here, then HFS, XFS and EXT are more likely to have a common data representation and I would not see this problem again?

---

