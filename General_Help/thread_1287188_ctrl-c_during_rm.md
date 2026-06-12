---
title: "ctrl-c during rm"
date: 2009-10-09
forum: General Help
---

### Post by bonfire89 on 2009-10-09
Soooo,

What happens if I start recursively deleting a folder then realize I shouldn't be and quickly hit ctrl-c?

Would there be partial/corrupt files lying around?

---

### Post by lloyd_b on 2009-10-10
> **bonfire89 said:**
> Soooo,

What happens if I start recursively deleting a folder then realize I shouldn't be and quickly hit ctrl-c?

Would there be partial/corrupt files lying around?

No.  "rm" either deletes the file or it doesn't.  When you "delete" a file, you are *not* erasing the data from the disk - you are just removing the directory entry for it, and telling the system that the disk blocks it formerly used are now free.

Lloyd B.

---

### Post by bonfire89 on 2009-10-10
fantastic.

it was a movies of folders. I don't mind having lost a couple movies.. but.. finding out that the movie is messed up an hour in to watching it would suck! hehe

Would that be similar to "mv"?


Thanks!

---

### Post by lloyd_b on 2009-10-10
> **bonfire89 said:**
> fantastic.

it was a movies of folders. I don't mind having lost a couple movies.. but.. finding out that the movie is messed up an hour in to watching it would suck! hehe

Would that be similar to "mv"?


Thanks!

Most filesystem routines (mv, rm, etc) work the same way.  The actual work of the routine is done via a "system call" (a call the the operating system kernel), which cannot be interrupted via <ctrl> C.  So using those keys to interrupt an operation will usually be an all-or-nothing proposition.

Note that if you <ctrl> C a program that's *writing* to a file, all bets are off...

Lloyd B.

---

### Post by bonfire89 on 2009-10-13
good to know!

thank you

---

