---
title: "Ext 3 Suicide"
date: 2009-11-19
forum: General Help
---

### Post by samurailink3 on 2009-11-19
Heya! I'm having a bit of a problem with an external hard drive that was formatted as Ext3 and was fishing for suggestions.. I mounted the drive today only to have it display nothing. Not one single file, BUT the drive does report the correct amount of free space. I've tried 'fsck.ext3 -f' on the drive, but to no avail. And helpful suggestions or a way to completely reindex the inodes of the filesystem? I'm pretty sure the data is completely in tact, as the drive reports the correct free space, but I'm pretty sure the file tree is corrupted.

How would I go about getting this back.

Insert sob story: Its a 1T media drive, I have 22G free :(

Thank you, helpful Linux Gods!

---

### Post by juancarlospaco on 2009-11-19
Palimsest
Photorec
Gparted

good luck

---

### Post by samurailink3 on 2009-11-19
Ok, looks like a bad superblock. How would I go about recovering this? 

Output of testdisk:
```
     Partition                  Start        End    Size in sectors

  ext3                           0 1953524655 1953524656
superblock 0, blocksize=4096
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096
superblock 2654208, blocksize=4096


```

---

### Post by samurailink3 on 2009-11-19
.

---

### Post by samurailink3 on 2009-11-19
Attempted all of these, nothing yet. Any more ideas? I'm sure the data is there, just need to rebuild the tree.

---

