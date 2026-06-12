---
title: "Restoring deleted files from an NTFS partition in Linux"
date: 2010-08-13
forum: General Help
---

### Post by IQAndreas on 2010-08-13
An older couple (good friends of mine) had their Windows installation crash (they should have been using Ubuntu in the first place ;)). They know the basics of how to use a computer, so they reinstalled Windows only to realize that EVERYTHING was replaced anew to factory settings. Now they are worried, and really want to know if there is some way to get all their pictures back.[


Yes, I know I could Google search for this, but I'm really not finding any good results. 98% of the results are for suspicious "Buy this magical program for all your recovery needs!"

**I'm wondering if there are any packages in the repository (or any programs that are guaranteed to be free of malware)** that will help restore deleted files from an NTFS partition?

All I need is a name, and I can find my way from there.


Cheers,
Andreas

---

### Post by earthpigg on 2010-08-13
> **IqAndreas said:**
>  Now they are worried, and really want to know if there is some way to get all their pictures back.[/COLOR]


All of them? almost certainly not. Some? Probably. Most? Maybe.

To maximize the number they do get back, tell them to stop using the computer. Do not boot from the hard drive until you've done what you can. Family pictures are important, so it's probably worth investing a great deal of time in:

Run photorec from a LiveCD. (Yes, you can install things from the repos when running from a LiveCD... it just won't stay.)

Documentation:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

both are included in the testdisk package.

Have the recovered data saved to an external hard drive. It will take quite a bit of time to sift through it all.

---

### Post by PRC09 on 2010-08-13
I hope this will help. I have not used these but I have seen Testdisk mentioned in other posts.....


[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by BobSongs on 2010-08-13
System Rescue CD (LINUX)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

If I were you, i'd browse Distrowatch.com

---

### Post by Mark Phelps on 2010-08-14
Having done data recovery a lot, my own experience summarizes as the following: MS Windows utilities work best on NTFS partitions; Linux utilities work best on Linux partitions.  Period.

The absolute best NTFS data recovery tools I've seen come from Runtime Software, in this case, GetDataBack for NTFS.  The free version will scan for, but not recover files.  So, you can use it to get a feel for how well it will work without having to pay for it.  To do the recovery, you have to purchase it.

I've gone the testdisk and photorec route, and their results were pathetic when compared to GetDataBack.

But hey, you get what you pay for ...

---

