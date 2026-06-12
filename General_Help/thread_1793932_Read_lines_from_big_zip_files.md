---
title: "Read lines from big zip files"
date: 2011-06-30
forum: General Help
---

### Post by lidengdeng on 2011-06-30
Hi:

How to see the first/last lines in a zip file (like head/tail commands)? The zip file only contains one file of big size.

Also, is it possible to read the lines from the zipped file one by one in C++ programming?

It's not a good idea to unzip it first due to its big size.

Thanks

---

### Post by Cheesehead on 2011-06-30
> **lidengdeng said:**
> How to see the first/last lines in a zip file (like head/tail commands)? The zip file only contains one file of big size.


'zcat' works like cat, but for zipped files.
```
zcat filename | head -1
zcat filename | tail -1
```

---

### Post by lidengdeng on 2011-06-30
> **Cheesehead said:**
> 'zcat' works like cat, but for zipped files.
```
zcat filename | head -1
zcat filename | tail -1
```

Thanks, that works.

And can we read the file one line by one line in C++ programming??

---

### Post by dFlyer on 2011-06-30
Please mark as SOLVED.

---

