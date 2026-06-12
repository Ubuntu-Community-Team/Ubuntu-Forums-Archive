---
title: "Raid5 File Space"
date: 2010-08-29
forum: General Help
---

### Post by ptmuldoon on 2010-08-29
I recently just grew my ext4 raid5 array this weekend adding another drive for a total of 5 1TB drives.

After the grow, tune2fs to 0, and resize, it shows now with a total of 3.64TB available.  Does this seem right?

I would have hoped to be getting close to the 4TB of them.

---

### Post by cascade9 on 2010-08-29
Seems normal to me. 

Dont forget that 1TB in HDD manufacturer =/= 1TB for everybody else. The HDD manufacturers use 1000B = 1KB, normally its 1024B = 1KB. They keep doing that all the way up to TB, so 1000KB = 1MB, 1000MB = 1GB, 1000GB = 1TB. 

Before anybody see this and comes in with the 'but 1024 is a kikibyte, etc, yes, I've seen that doublethinking, and disagree. If somebody does want  a base 10 counting method, then fix stage one...8 bits to the byte, shouldnt there be 10? ;)

---

### Post by ptmuldoon on 2010-08-29
Ok, thanks.  

My other issue is that the mapped raid drive on my home (windows) machines is seeing the raid as only 7GB capacity, and not the 3.64TB.

This is likely a windows issue, and I'm googling around to try and learn its cause, but any help would be greatly appreciated.

PT

---

