---
title: "Imaging with dd"
date: 2012-06-16
forum: General Help
---

### Post by Jonny87 on 2012-06-16
If I Image a drive with the likes of dd (or anything else if someone can recommend something) will that image include the data of deleted files etc. The sort of thing that one would look to recover with testdisk recovery software?

I want to image a disk as I want to do a fresh install on it. But I want to at a later point in time also recover anything I can that was ever on that drive. My reasons for this are complicated and involve complex family matters. So want copy not just the current data but all pre-existing data.

If so are specific parameters that need to be used?

---

### Post by jwbrase on 2012-06-17
> **Jonny87 said:**
> If I Image a drive with the likes of dd (or anything else if someone can recommend something) will that image include the data of deleted files etc. The sort of thing that one would look to recover with testdisk recovery software?

I want to image a disk as I want to do a fresh install on it. But I want to at a later point in time also recover anything I can that was ever on that drive. My reasons for this are complicated and involve complex family matters. So want copy not just the current data but all pre-existing data.

If so are specific parameters that need to be used?

It will copy any data from deleted files that hasn't yet been overwritten. Deleting a file just causes the computer to forget where it put the file and mark the space taken up by the file to be marked as unused, but leaves the data in place. However, any subsequent creation of a new file (or write to an old one that is longer than it was the last time it was written to) may cause part or all of a deleted file (or even multiple deleted files) to be overwritten, in which case dd will pick up the new data instead of the old data.

Nothing, other than imaging the entire drive, is needed for dd to pick up old data that hasn't yet been overwritten (you'll still have to run testdisk to find it, of course), and nothing can be done to cause it to pick up the old data instead of the new in the case of data that has been overwritten.

---

