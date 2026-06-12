---
title: "Unable to extend unallocated space into windows partition"
date: 2011-08-05
forum: General Help
---

### Post by georgeos on 2011-08-05
So I booted into GParted, and shrunk my Ubuntu partition by 100gb today,  in the hopes that I would be able  to extend my Windows partition.  However GParted won't let me extend  this unallocated space into my  Windows partition. I booted into  Windows, and still no luck, I tried  EASEUS partition manager, which  didn't work.  So I shrunk my current Windows partition (within windows)  by about 1gig  to check if I could re extend it. And what I found was  that the new  unallocated space seemed to be separate from the 100gb  unallocated  space, they wouldn't merge. But I was able to re extend  that 1gig back  to the Windows partition.
So does any one have any idea how I can extend this 100gb of unallocated space into my windows partition?

---

### Post by pastalavista on 2011-08-05
You just need to format the unallocated space as ntfs and when you next boot into Windows, it will recognise it and assign it a Windows drive letter.

---

