---
title: "Recovering Deleted files"
date: 2010-04-20
forum: General Help
---

### Post by gk_manutd on 2010-04-20
Hello all....

I spent 5 days doing a class assignment, and accidentally deleted the whole set of files.

The files were of type .cpp and a .h file and a makefile.

How do I recover these from Ubuntu? I'm running 9.10, and currently I am using the 9.04 live CD to do this:

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)


Assuming this works, how do I figure out which files are the ones that I need?


Please, please help me out.

---

### Post by OriginalName on 2010-04-20
I'm afraid you have to go through each one to see if it's the one you need... the filenames are lost!

---

### Post by P4man on 2010-04-20
You could use grep on them if you know some keyword that would occur in the text files you are looking for.

---

### Post by gk_manutd on 2010-04-20
Thanks guys.

But my immediate concern is actually recovering those files. I can't manage to. Any suggestions?

---

### Post by clhsharky on 2010-04-20
HI gk_manutd

Use TestDisk or PhotoRec with Ubuntu, in repos.
Or
Download and burn Parted Magic and use TestDisk or PhotoRec.

Parted Magic has many very useful tools and Id start with PhotoRec.
It recovers way more than photo's

Sharky

---

### Post by P4man on 2010-04-21
> **gk_manutd said:**
> Thanks guys.

But my immediate concern is actually recovering those files. I can't manage to. Any suggestions?

Might help if you give some more information where you are stuck. You are following the psychocat's how to?

---

### Post by gk_manutd on 2010-04-25
Yes. 

I recovered a most of the files... but they've turned into gibberish... some are even completely empty.

---

### Post by john newbuntu on 2010-04-25
Now, how long was it between the time you accidentally deleted the files until you shutdown the computer for recovery?  If this was immediate, you could have recovered most of the files intact.  Otherwise, there is a very good possibility of some of these files getting overwritten or even getting lost.

---

### Post by gk_manutd on 2010-04-26
Its been a few days. That must be the reason- overwriting. I recovered a lot of the files... but I was a little surprised. Isn't there an oldest first algo or something? I didn't expect files deleted 10 hours ago to be overwritten.
:(

---

### Post by john newbuntu on 2010-04-26
ext* filesystems and Ubuntu try to randomize data and spread it across the disk to reduce fragmentation and maintain an optimal disk I/O.  I do not know the deletion/creation algorithm but certainly do not expect it to be a simple queue/FIFO order.  Although less likely, you can even expect files deleted a few seconds ago to be overwritten!  

To prevent accidental erasure, use the trash to recover files quickly.  If you are using a terminal, create an alias to move files to trash rather than deleting them through rm.

---

### Post by P4man on 2010-04-26
Not much use to the OP, but he has a point. rm just works too well. It would be nice if linux were a bit more user-error tolerant here.

---

### Post by gk_manutd on 2010-04-26
Thanks guys- all of you!

Like I said, I managed to recover the files.. but they were either empty or gibberish. If nothing else, this has been an interesting experience.

@john newbuntu: The alias part sounds like a good idea. Thanks!


I'm giving up on this- I've overwritten what I need. :(


Thanks again! I really appreciate it.


For anyone else who follows suffers from the same problem, and comes looking into this thread:

DO NOT INSTALL RECOVERY TOOLS ON DISK. Use a LiveCD.

I used R-Linux to recover files. It works. Google it.

---

