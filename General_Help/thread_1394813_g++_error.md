---
title: "g++ error"
date: 2010-01-31
forum: General Help
---

### Post by Dr Belka on 2010-01-31
So I started learning C++ yesterday.  I have learned some of the basics, thats all.  

But, I have started to notice that after I have worked for a little while, and compiled several .cpp files, I started getting this error when trying to run "gcc" or "g++"

/usr/bin/ld: final link failed: No space left on device
collect2: ld returned 1 exit status

I have found no way to fix this other than restarting my pc.  After that, it works just fine.

Any ideas?

---

### Post by rnerwein on 2010-01-31
hi
to restart your box isn't a good solution. "what good is comes back". so have to look where your disk-space is going. ld tould you:  No space left on device: use df -k or du -k on your system. often people ain't look in there trash directory. it's possible that there are a lot of files you had removed via your desktop - but they are still on disk.
ciao

---

### Post by nunoxic on 2011-09-13
Had a similar problem. Emptying trash Solved it.

---

