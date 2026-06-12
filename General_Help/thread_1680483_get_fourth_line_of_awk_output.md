---
title: "get fourth line of awk output"
date: 2011-02-02
forum: General Help
---

### Post by ntesla123 on 2011-02-02
How do I get the fourth line of the output of awk?

If the output is:

345
456
643dd3
adljf898

How do I get the fourth line so that output would be "adljf898"

---

### Post by sisco311 on 2011-02-02
Try something like:
```
awk "NR==4{print;exit}" file
```

See also:
[http://mywiki.wooledge.org/BashFAQ/011](http://mywiki.wooledge.org/BashFAQ/011)

---

