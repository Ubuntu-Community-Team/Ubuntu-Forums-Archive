---
title: "Why such a latency when saving on removable media?"
date: 2009-08-02
forum: General Help
---

### Post by merciadriluca on 2009-08-02
Hello,

Only when using Ubuntu (not ``pure Debian''), a strange phenomenon occurs when I want to save data on a removable media, such as a usb key. Let's say that I want to copy a simple file, i.e. a text file, on my usb key. I plug it in, waits for it to be mounted. Then, I make cp operations. I have a LED on my usb key, which is turned on only when I/O operations are done on it. 
Once I have done, e.g. ```
cp foo.bar /media/my_key/
```, the led lightens a little while, then stops. After ~50 seconds, it lightens a little while. It then stops. After ~15 seconds (after the ~50 past and last seconds), it lightens for the last time a little while.

I notice that data is present on the usb key only after the first waiting period (~50 seconds), using ls. It is very strange, and my usb key is not faulty at all, as this problem occurs with other usb keys, other storage drives, ...

Note that it only happens on Ubuntu. I do not have the problem under Debian.

Is there a similar report for other users?

Thanks a lot.

---

