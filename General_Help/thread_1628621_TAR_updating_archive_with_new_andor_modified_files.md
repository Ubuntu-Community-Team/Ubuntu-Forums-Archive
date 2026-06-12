---
title: "TAR updating archive with new and/or modified files"
date: 2010-11-22
forum: General Help
---

### Post by slooksterpsv on 2010-11-22
Is there anyway to (I believe it's called a Differential backup, but all the scripts I could find were doing it as incremental which didn't make sense for calling it differential, again I could be wrong) do a backup with tar archives where instead of recreating the entire archive, it just updates it and replaces modified files as well as inserts new files into the archive?

Example:
temp1.tar.gz contains-
file1.txt - mod 9/22/2010
file2.txt - mod 9/22/2010

we modify file2.txt and create file3.txt so when we update the archive it does:
file1.txt - mod 9/22/2010
file2.txt - mod 11/22/2010
file3.txt - mod 11/22/2010 

2 files replaced, file2 and file3, no new archive created or that.

The reason I ask is cause I have huge folders, like 50GB in size, and I'd rather do a differential backup (I'm calling it that due to the meaning I found it states as updating a backup with modified files)

---

### Post by slooksterpsv on 2010-11-22
Nevermind, I have to recreate the archive to compress it :(. Oh well...

---

