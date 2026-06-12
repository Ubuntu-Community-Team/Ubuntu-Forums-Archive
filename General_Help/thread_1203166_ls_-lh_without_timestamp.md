---
title: "ls -lh without timestamp"
date: 2009-07-03
forum: General Help
---

### Post by earthmeLon on 2009-07-03
I would like for ls to output similar to **ls -lh** but I would like it to do so without spitting out timestamps.

Any help would be greatly appreciated :D

---

### Post by Despite on 2009-07-03
Try:```
ls -lh --time-style=+
```--time-style tells it how to format the timestamps, + tells it to use date style formats, and then you give it no format to use.

---

### Post by earthmeLon on 2009-07-03
> **Despite said:**
> Try:```
ls -lh --time-style=+
```--time-style tells it how to format the timestamps, + tells it to use date style formats, and then you give it no format to use.

Thanks man!  When I did **ls --time-style=** with no definition the first time, it gave me 4 options (something about iso and local and some stuff)

I didn't realize there were more options.  :D

---

