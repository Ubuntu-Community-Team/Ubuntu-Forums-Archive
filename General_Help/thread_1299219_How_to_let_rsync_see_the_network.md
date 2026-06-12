---
title: "How to let rsync see the network?"
date: 2009-10-23
forum: General Help
---

### Post by DeMus on 2009-10-23
I have made back-ups using grsync, the graphical interface for rsync, from my home folder to an external USB disk. This works fine.
Now I also want to do that for files on my wife's computer. I need to let (g)rsync see the network share and copy from that to the USB disk.

How do I do that? When in grsync I can not choose a network drive, it simply is not in the list.

I have Samba working, that's not a problem. How can I make grsync see my network?

---

### Post by DeMus on 2009-10-24
I know 7 hours is not long but I will bump this thread anyway. I sure would like an answer.
I have been trying to mount the network share into /mnt but that didn't work.
Please help me guys, I need your help.

---

### Post by blwizard on 2009-10-24
Don't know if this will work, but try creating a soft link in your home folder for the network drive. and you should be able to see the link within grsync.

---

### Post by fisheater on 2009-10-24
Have a look at this thread, I had a similar problem.

[http://ubuntuforums.org/showthread.php?t=1217797](http://ubuntuforums.org/showthread.php?t=1217797)

This is a very useful guide:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Good luck

FE

---

### Post by DeMus on 2009-10-24
> **fisheater said:**
> Have a look at this thread, I had a similar problem.

[http://ubuntuforums.org/showthread.php?t=1217797](http://ubuntuforums.org/showthread.php?t=1217797)

This is a very useful guide:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Good luck

FE

Fantastic. I followed your second link, first post and it worked wonders.
Thank you very much.

---

