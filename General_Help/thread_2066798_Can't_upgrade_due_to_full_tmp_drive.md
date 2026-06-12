---
title: "Can't upgrade due to full /tmp/ drive"
date: 2012-10-05
forum: General Help
---

### Post by tbrminsanity on 2012-10-05
Good day everyone,

Recently when I tried to update my server (using apt-get upgrade), I was getting a weird error.  There were several output lines that stated the /tmp/ was out of memory.  When I rand df it confirmed that both my primary partition and /tmp/ partition were at 100% capacity (even though my hargest directory was only about 50% capacity).  After some investigation using Disk Usage Analyzer, I discovered that my primary user folder was sucking up over 90% of my disk space.  I was able to narrow this down to one file:
.xsession-errors-old

When I deleted the file, my problem disappeared.  I hope this helps others with this issue in the future.

---

### Post by CrusaderAD on 2012-10-05
Thanks for the pointers. You can also run:

```
sudo apt-get clean && sudo apt-get autoclean
```

To free up some space.

---

