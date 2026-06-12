---
title: "View largest directory in Command Line"
date: 2010-07-08
forum: General Help
---

### Post by sr_guy on 2010-07-08
What is the quickest way to get a list of directories that have 500MB or more of content?

du | grep ???? 

or am I way off?

---

### Post by DaithiF on 2010-07-08
Hi,
no doubt there are better ways than this, but since I can't think of any:
```
find . -type d -exec du -Sk {} \; | sort -rn | awk '$1 < 500 { exit }; 1;'

```

---

