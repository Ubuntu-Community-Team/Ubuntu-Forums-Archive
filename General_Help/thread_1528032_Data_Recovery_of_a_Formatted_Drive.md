---
title: "Data Recovery of a Formatted Drive"
date: 2010-07-10
forum: General Help
---

### Post by COKEDUDE on 2010-07-10
Could I please have some recommendations for Data Recovery of a Formatted Drive. There are so many choices out there that I don't know which one I wanna use.

---

### Post by yetiman64 on 2010-07-10
> **COKEDUDE said:**
> Could I please have some recommendations for Data Recovery of a Formatted Drive. There are so many choices out there that I don't know which one I wanna use.

Testdisk, available from the repositories is one possible option.

Here's a link to the CG Security site for step by step instructions [--LINK--]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by balaknair on 2010-07-10
> **yetiman64 said:**
> Testdisk, available from the repositories is one possible option.

Here's a link to the CG Security site for step by step instructions [--LINK--]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

I second that.
testdisk has helped me save quite a few friends' data after their hdds failed(and of course, they hadn't made any backups).

---

### Post by bumanie on 2010-07-10
+1 for testdisk - it should be able to retrieve your original partitions as they were prior to the format. If not, you will be able to get most, if not all the information back with photorec, which is part of testdisk - photorec can search for 100+ file types and reads the data off the raw hard drive and is thus, filesystem independent. In the repo's there is also a program called magicrescue that does much the same thing. If the filesystem was NTFS, you could use the ntfsprogs program, called ntfsundelete.

---

### Post by COKEDUDE on 2010-07-10
> **bumanie said:**
> +1 for testdisk - it should be able to retrieve your original partitions as they were prior to the format. If not, you will be able to get most, if not all the information back with photorec, which is part of testdisk - photorec can search for 100+ file types and reads the data off the raw hard drive and is thus, filesystem independent. In the repo's there is also a program called magicrescue that does much the same thing. **If the filesystem was NTFS, you could use the ntfsprogs program, called ntfsundelete.**

It was a NTFS file system before I formatted the drive. Then I split the HD into 2 partitions. Then I made a XP partition and a Ubuntu partition. After I did that I realized I forgot some pictures that I was supposed to backup.

---

