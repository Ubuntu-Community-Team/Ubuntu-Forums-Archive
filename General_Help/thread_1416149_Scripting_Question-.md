---
title: "Scripting Question-"
date: 2010-02-25
forum: General Help
---

### Post by blur xc on 2010-02-25
Say I'm using the find command to locate and copy a set of files from one or more directories, what's the best way to verify that the copy was successful?  

I can do a "find /blah/blah -type f | wc -l" for the source and destination after they copy is complete, and that will tell me if the destination has the same number of files as the source does, but what about bytes?  What if a file is corrupted and not all of it transfered?  Is there any way to do a comparison of bytes copied?

Thanks,
BM

---

### Post by falconindy on 2010-02-25
This should work:

```
comm <(du /path/to/orig) <(du /path/to/backup)
```

A more robust solution would be something along the lines of...

```
cd /path/to/orig
find -type f | while read file; do
  cmp $file /path/to/copy/$file
done
```
'cmp' is a byte by byte file comparison tool.

---

### Post by blur xc on 2010-02-25
> **falconindy said:**
> This should work:

```
comm <(du /path/to/orig) <(du /path/to/backup)
```A more robust solution would be something along the lines of...

```
cd /path/to/orig
find -type f | while read file; do
  cmp $file /path/to/copy/$file
done
```'cmp' is a byte by byte file comparison tool.

Sweet!  thanks, I'll study up the man pages from cmp.

BM

---

