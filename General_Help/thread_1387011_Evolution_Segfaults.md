---
title: "Evolution Segfaults"
date: 2010-01-21
forum: General Help
---

### Post by Skip Da Shu on 2010-01-21
v9.10, x86_64

After update manager ran today I can't start evolution.  I found this in messages:
 ```
Jan 21 10:27:53 c17-desktop kernel: [ 1482.902545] evolution[4166]: segfault at 0 ip 00007fb1a0a3bc90 sp 00007fff29db6d78 error 4 in libglib-2.0.so.0.2200.3[7fb1a09de000+c5000]
```

I've got no idea how to resolve.  From Synaptic I've done:  reinstall libglib-2.*, reinstall evolution

I did have proposed and backports repositories on.  I removed proposed before doing the reinstalls.

I'm sure there's probably something in ./evolution I can delete to be able to read my email (I have nothing of value in the calandar) but I don't know what to delete.

---

### Post by crh0831 on 2010-02-01
I had a similar problem with libglib segfaulting after recent updates.  I've done a bunch of reading and have seen that the new version of libglib2.0 is always involved.  Rolling it back to the previous version fixed my problems.  It's only a work-around, but it may help until to the problem gets sorted.

See this thread: [http://ubuntuforums.org/showthread.php?t=1395237](http://ubuntuforums.org/showthread.php?t=1395237)

---

