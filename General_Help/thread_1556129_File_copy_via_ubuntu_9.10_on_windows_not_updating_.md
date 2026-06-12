---
title: "File copy via ubuntu 9.10 on windows not updating directory tree"
date: 2010-08-19
forum: General Help
---

### Post by anirudhtomer on 2010-08-19
hi everyone,

I have ubuntu 9.10 &  windows 7 on my laptop. I have one 40GB Primary partition (C:) & 60 GB logical partition on my windows. I have given another 20GB for ubuntu.

I hibernated my windows7 & then started ubuntu 9.10. Then I copied a folder containing some PDF files from my ubuntu to that 60GB (D:) on windows. Then I rebooted the machine & choose windows from GRUB. the windows came up from hibernation but nowhere I was able to see that folder which I copied.

Since ubuntu supports (understands) NTFS file system it means when I copied that folder it should have updated the Directory Tree of NTFS on that 60GB (D:) but that folder is not shown.
When I restart the windows the folder appears (ofcourse because windows checks the file system again for consistency while in hibernation it does not).

A few months earlier I had windows XP & that time this does not happened to me ever.

I want to know  the exact reason behind such behaviour. 

Thanks in advance

---

### Post by Redblade20XX on 2010-08-19
I think its a security reason to why you are getting locked out of those file access. Sharing between OS's like that can lead to vulnerabilities.

---

### Post by anirudhtomer on 2010-08-19
but if the file is being copied & if ubuntu understands NTFS then it must have made changes in the DIRECTORY TREE for sure & if so then as soon as windows comes up from hibernation it should show that folder when I try to access the parent directory of that copied folder.

---

### Post by anirudhtomer on 2010-08-19
may be the Directory tree of the NTFS is left in READ ONLY mode at hibernation. 
That's why I can see the files on NTFS & copy there too but the changes won't be applied to directory tree. so when the windows comes up it can't see the files there & when it restarts it builds up the tree again & I get to see my files.

but thinking technically this thing is illogical. I am just trying to think of possible solutions. Any help would be appreciated.

---

