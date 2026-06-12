---
title: "Writing data back to a damaged hard disk"
date: 2009-07-07
forum: General Help
---

### Post by wellilein on 2009-07-07
Hi.

I've recently been doing some data rescuing with Ubuntu and Windows. At first I have made an IMG file with DD_RESCUE. Then I did various data recovery which was really successful. My last try was using Windows CHKDSK. Of course I could not do this on the IMG file and I needed to use the real disk.

Now the disk content has changed from what I have received. My client wants the hard disk back, but in its original state (for whatever reason... don't ask). Seems easy, I just tried DD to push the IMG back on the hard disk. 

Unfortunately the disk has write problems. Is there a way to ignore write errors with DD or DD_RESCUE?

Seriously: I want to write as much data as possible to a damaged hard disk. I am very aware of that the data is not safe there.

Thank you so much!

---

### Post by Jebtrix on 2009-07-07
Example:
dd if=/dev/hde of=/dev/hdf conv=noerror,sync

---

### Post by sedawk on 2009-07-07
You can try to write the disk block by block.

With "dd" you need options
blocksize=512 : default block size of HDDs
skip/seek : to move read and write position to correct position first.
count=1 : write exactly one block

If you know how many blocks are on the disk you can do this block
by block and ignore errors in between.

(a more sophisticated way might be to try bigger "chunks" first,
 e.g. if writing 100% doesn't work, split the task in 50/50 and
 try again. If 50% fails (one or both) split that one again into
 25/25 and try again. You can do this down to blocks or even
 bytes - although I'm not sure it makes sense to try a deeper
 level then blocks of 512 bytes. )

I think it is a rule of thumb that write errors will get more
and more, so writing to an already faulty disk is a funny thing to do.

---

### Post by Jebtrix on 2009-07-07
Just one other possible (long winded one) solution is to run the drive manufacturers diagnostic software. Some of them will ask to remap bad sectors.

---

### Post by wellilein on 2009-07-08
From "dd --help" I see that conv=noerror will ignore read errors. Actually my second try with conv=noerror succeeded. However I am not sure whether this is due to ignoring errors or whether the hard disks fault management has meanwhile replaced the bad block by a spare block...

---

