---
title: "A Question about bidirectional synchronization"
date: 2010-05-06
forum: General Help
---

### Post by Andreas1 on 2010-05-06
Hi,

i have a question concerning file/folder synchronization. Currently, i use rsync via ssh to backup my personal data to my old laptop:

```
rsync -ahv --delete -e ssh /media/data/andreas andreas@oldlaptop:/media/data/andreas
```

this obviously goes one way, new laptop --> old laptop. now i thought i'd make it work both ways, so i can edit/create documents on the old laptop too. some googling tells me that *unison* is what i want to use, but before i can do so, i want to understand something:

if a certain file is different in the two places, i assume the one with the newer timestamp overwrites the older one. but: what happens if a certain file only exists in one place? how can unison (or any other tool, for that matter) determine whether the file was newly created in place A (and copy it to place B), or recently deleted in place B (and thus delete it from place A)?

---

### Post by dcstar on 2010-05-06
> **Andreas1 said:**
> 
........
if a certain file is different in the two places, i assume the one with the newer timestamp overwrites the older one. but: what happens if a certain file only exists in one place? how can unison (or any other tool, for that matter) determine whether the file was newly created in place A (and copy it to place B), or recently deleted in place B (and thus delete it from place A)?

When you first use Unison it creates a database with all the files you originally copy, so if a file then is removed from either location it deletes the other copy as well.

---

