---
title: "quick sys admin"
date: 2010-06-16
forum: General Help
---

### Post by goseph on 2010-06-16
Hi everybody!

I have a long series of folders containing thousands of random files. What I want to do is sort them according to file type eg. one folder full of .mp3, one folder of .jpgs, .doc etc. etc.

What command will sort this out for me?

---

### Post by amauk on 2010-06-16
```
cd /top/level/directory
find . -type f -iname '*.mp3' -exec mv {} /path/for/mp3s \;
find . -type f -iname '*.doc' -exec mv {} /path/for/docs \;
...
..
```

---

### Post by goseph on 2010-06-16
Thankyou very much!

---

