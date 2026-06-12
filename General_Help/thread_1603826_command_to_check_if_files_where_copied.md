---
title: "command to check if files where copied"
date: 2010-10-23
forum: General Help
---

### Post by jarrah-95 on 2010-10-23
i am trying to write a script to copy all of my photos to my backup drive, to finish it i want to scan the backup and check that all of the folders and photos are there. is there a command in linux to do this (theres one (or two) for everything else!!!)
thanks

---

### Post by gmargo on 2010-10-23
Use **md5sum** (or sha1sum or sha256sum).  Generate the checksum file on the source side and copy that along with the data.  Then check on the destination side.

Here's the sort of command I use all the time.  This will generate the MD5SUMS file.
```

find . -type f -print | sort | grep -v "^\./MD5SUMS" | tr '\n' '\0' | xargs -0 md5sum -b | tee MD5SUMS-20101023.txt

```And on the destination side just use the -c option to check:
```

md5sum -c MD5SUMS-20101023.txt

```

---

