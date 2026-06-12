---
title: "Missing critical shared libraries becoming corrupted? No longer valid ELF binaries"
date: 2010-05-30
forum: General Help
---

### Post by Mr. Picklesworth on 2010-05-30
Hi! Fascinatingly weird one here. First, this issue isn't on my computer, it's from someone who I am helping. I don't have first-hand access to the computer.

Some background: the machine originally had Ubuntu Hardy, which we upgraded to Lucid a couple of weeks ago.

Earlier this week, he gave me a call that Ubuntu wasn't booting up; it dropped to the command line. Some tinkering later, I figured out that libgthread-2.0.so had become corrupted, so X wasn't starting. It gave an error complaining that it had an invalid ELF header.
I figured that this was just an odd freak occurrence; there was a bad kernel panic previously, so maybe the library was upgraded and the system was just writing to the disk at that time.
Fixed via sudo aptitude reinstall libglib.

Ubuntu then started and everything ran perfectly.

Today, he gave me a call. After he had restarted the computer, Ubuntu again dropped to terminal at the same point while booting. I had him open a new tty and run startx, which failed with a different shared library but the same error: *libXext.so.6* has an invalid ELF header!

We had run updates, but I don't recall whether X's shared libraries were touched. Even if they were, though, that shouldn't affect anything. There were no hard resets between my fixing libgthread and libXext breaking.

And yes, I'm going to try a clean install; I'm really just hoping we can figure out why this is, because it's an amazing little problem.
Any ideas? :)

---

### Post by ezsit on 2010-05-30
I sense hardware failure, in the very near future, possibly hard drive developing bad sectors? Watch! Falling rocks ahead! :-)

---

### Post by sdennie on 2010-05-30
A hard drive failure is indeed a likely culprit.  I would also check the modification time on the file it's complaining about.  If it's not recent, that strongly suggests disk failure.

---

### Post by Mr. Picklesworth on 2010-05-30
The curious thing is it was a single library the first time, and on both occasions it has been a library that X uses; the system makes it to that level and can proceed to run a terminal *with networking* without any issue.
(I'm not sure if it was one or more libraries the second time. Being pressed for time, I tried reinstalling libxext6, it didn't magically fix everything, so I started a clean install).

I wonder if it's a driver acting up? (Currently using the Nouveau driver to push the NVidia hardware on an HP dv9000).

Thanks for the tip about modification date, though. Unfortunately I've already replaced the library myself at this point, but that reminded me to check apt's history.log. It says libxext has not been upgraded in recent history. So, that rules out apt as a suspect.

---

### Post by sdennie on 2010-05-30
> **Mr. Picklesworth said:**
> 
I wonder if it's a driver acting up? (Currently using the Nouveau driver to push the NVidia hardware on an HP dv9000).

Thanks for the tip about modification date, though. Unfortunately I've already replaced the library myself at this point, but that reminded me to check apt's history.log. It says libxext has not been upgraded in recent history. So, that rules out apt as a suspect.

It sounds like either a failing disk or some very low level filesystem corruption.  You could try booting into single user mode and forcing a filesystem check.  If all is well and the problem persists, it's most likely hardware.  The file modification times might be useful because that information is not stored in the same place on disk as the file.  If the file has obviously changed but the modification time is old and the fsck says all is well, I'd replace the disk.

---

