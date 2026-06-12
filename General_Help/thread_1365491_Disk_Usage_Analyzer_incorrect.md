---
title: "Disk Usage Analyzer incorrect?"
date: 2009-12-27
forum: General Help
---

### Post by shendric on 2009-12-27
So, I've run Disk Usage Analyzer on my filesystem, which uses a 500G SATA drive.  According to the upper message on DUA, the total filesystem capacity is 449.2 GB (used: 409.1 GB available: 40.1 GB).  This doesn't seem realistic to me, and it's further mystifying, because the home folder (the largest user of disk space), says that I'm using 82.GB of space.  The other folders use just smaller amounts of space.

So, where's the rest of my hard drive space?

Thoughts?

---

### Post by s.fox on 2009-12-27
Hello,

I think the discrepancy between the 500 and 449.2 is to do with definition of what a gig actually is.  [Here]("http://www.brettbits.com/Text/MissingHardDriveSpace/") is some reading that should explain.  If you have any more questions on this topic then please post back :)

-Silver Fox

---

### Post by shendric on 2009-12-27
> **Silver_fox_ said:**
> Hello,

I think the discrepancy between the 500 and 449.2 is to do with definition of what a gig actually is.  [Here]("http://www.brettbits.com/Text/MissingHardDriveSpace/") is some reading that should explain.  If you have any more questions on this topic then please post back :)

-Silver Fox

Hey,

Thanks for the response.  The difference between the 500 and 449.2 isn't what concerns me, though.  I expect that level of discrepancy.  What concerned me was the missing ~400G of space.  However, I seem to have found it.  They were backup files in the root directory that weren't showing up in DUA.

---

### Post by dcstar on 2009-12-27
> **shendric said:**
> Hey,

Thanks for the response.  The difference between the 500 and 449.2 isn't what concerns me, though.  I expect that level of discrepancy.  What concerned me was the missing ~400G of space.  However, I seem to have found it.  They were backup files in the root directory that weren't showing up in DUA.

Running user privilege programs will not show files that the user has no rights to access:
```
gksudo baobab
```

---

### Post by shendric on 2009-12-28
> **dcstar said:**
> Running user privilege programs will not show files that the user has no rights to access:
```
gksudo baobab
```

I'm pretty sure I ran baobab as root, and it still didn't show those backup files.  *shrug*

---

### Post by paul2909 on 2010-01-17
My hard drive is 80gb but when i go into it, it says that the total size is 22.2.
Does anyone have a solution for this?

---

