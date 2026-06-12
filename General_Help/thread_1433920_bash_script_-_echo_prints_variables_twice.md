---
title: "bash script - echo prints variables twice"
date: 2010-03-19
forum: General Help
---

### Post by Vyder on 2010-03-19
Hi

I'm writing a bash script, and attempting to print out the date and timestamp on a folder.

I'm isolating the two variables and printing it out, but its printing twice.

```
printf "LATE submission: "
#Find how late
date=`ls -l late | grep $id | cut -d" " -f6`
timestamp=`ls -l late | grep $id | cut -d" " -f7`
printf "$date - $timestamp\n"
```

Terminal Output:
```
LATE submission: 2010-03-19
2010-03-19 - 02:12
02:12
```

Any idea why?

-Vyder

---

