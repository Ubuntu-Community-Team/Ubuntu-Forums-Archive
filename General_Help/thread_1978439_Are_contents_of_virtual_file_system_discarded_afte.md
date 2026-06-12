---
title: "Are contents of virtual file system discarded after shutdown?"
date: 2012-05-11
forum: General Help
---

### Post by akshay.sulakhe on 2012-05-11
Hello friends,
              I just wanted to know,when we shutdown the system(normally),are the contents of shutdown discarded. I am specifically asking about subdirectories under /proc and /sys . Kindly let me know,i googled,but couldnt find the answers. Thank you for your time. :-)

---

### Post by Monotoko on 2012-05-11
/proc is basically a way into your kernel, a new copy is put into memory on boot up. (For example you can write badly to it, have a kernel panic, and boot up fine next time) /sys is the same, but it provides a lot of non-process information (such as drivers)

So yes, because they are reading from memory and memory is refreshed at bootup :)

---

