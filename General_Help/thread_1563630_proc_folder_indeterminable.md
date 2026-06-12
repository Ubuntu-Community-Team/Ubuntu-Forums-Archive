---
title: "proc folder indeterminable"
date: 2010-08-29
forum: General Help
---

### Post by a sandwhich on 2010-08-29
I have ubuntu install on a 500 gb drive. It says i have 409 gb free. I've been able to account for 40 gb, but when I try to check the folder proc, it lists 128 tb. How much space is this folder actually taking up?

---

### Post by Rubi1200 on 2010-08-29
You can check using the ```
df -H
``` command in the terminal for the whole drive and from Applications > Accessories > Disk Usage Analyzer run a scan on the whole computer to see the size of each folder.

Also, you can cd into the directory and run ```
du -hs
```

---

