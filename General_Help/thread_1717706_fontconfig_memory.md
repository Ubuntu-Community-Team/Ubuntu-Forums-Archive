---
title: "fontconfig memory"
date: 2011-03-30
forum: General Help
---

### Post by max5555 on 2011-03-30
My Ubuntu consumes too much memory. I have checked it with memstat and have found a lot of lines like these:

```
    4k(      4k): /home/user/.fontconfig/14d03e56f5e4fbef7684ac4366c0529a-le32d4.cache-3 1543 1571 1582 1583 1585 1586 1590 1599 1612 1627 1666 1833 1838 1839 1857 1870 1872 1875 3687 3892 4026 4051 4056 4226 4233 8657 9160
     12k(     12k): /home/user/.fontconfig/239134a7fc11cf64e243959017b1a4c3-le32d4.cache-3 1543 1571 1582 1583 1585 1586 1590 1599 1612 1627 1666 1833 1838 1839 1857 1870 1872 1875 3687 3892 4026 4051 4056 4226 4233 8657 9160

```

There are more than 480 lines like this! What are these fontconfigs for? Where do they come from?

---

### Post by ChipOManiac on 2011-03-30
I don't know what's happening. But .fontconfig has the details needed to display some fonts correctly, it shouldn't take this memory since it's just like an xml... :O

---

### Post by max5555 on 2011-03-30
More than 480 "details" to dispaly "some" fonts? Isn't it too much?

---

### Post by ChipOManiac on 2011-03-30
> **max5555 said:**
> More than 480 "details" to dispaly "some" fonts? Isn't it too much?
 
Yes, Pretty INSANE. Open Up The Files In A Text Editor And See What's Happening... Just In Case... :|

---

