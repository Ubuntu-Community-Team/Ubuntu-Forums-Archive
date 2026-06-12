---
title: "Queueing copy to USB key"
date: 2010-05-13
forum: General Help
---

### Post by yankeeDDL on 2010-05-13
Hi,

I have accidentally started to copy two large files from the HD to a USB key.
I say "accidentally" because with Windows and it's lousy "Explorer" having 2 (or more) concurrent I/O operations on a USB key causes a tremendous slowdown of the operations.
Meaning, say it takes me 5 minutes to copy a file to the Key. 2 files in sequence would take me 10 minutes, but in parallel, this can go on for as long as 1hr.
Just before giving up Windows I found out that most 'alternative' file managers (Total Commander, to name one), have instead a queuing system that automatically queues I/O operations towards the same device. 

Well, in Ubuntu I had the same exact problem: two concurrent I/O operations are parallelized and as a result it takes ages to actually perform the operation.

Is there a way to set the file manager so that it automatically queues the operations to the same device?

Thanks!

---

