---
title: "The system cant find the second partition?"
date: 2009-11-02
forum: General Help
---

### Post by anicaus on 2009-11-02
Hello all! :D

Finally I have decided to install Ubuntu alongside Windows. A positive experience so far! There is one issue I have though (and that is why I am here of cource). 

My primary drive have two partitions. Windows and lots of stuff on the first partition and linux and lot of stuff on the second one.
The thing is that when I am using Ubuntu I can find the windows partition, but not the Linux one. 
There is probably an easy solution to this?

I am using a rather new acer laptop, all drivers found. Ubuntu 9.10 64bit. I installed Ubuntu FROM Windows by the help of PowerISO (viritual drive). Installation went flawless and no error messages.

Thanks for any help and let me know if further config info is required to troubleshoot!

---

### Post by geirha on 2009-11-02
In wubi-installs, the filesystem where the virtual ubuntu drive is located will be permanently mounted at /host (if I remember correctly), so take a peek in there and see if you recognize it as your second partition.

---

