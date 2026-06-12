---
title: "Top Batch Mode"
date: 2009-11-14
forum: General Help
---

### Post by bluTaz on 2009-11-14
Had a question guys. Was playing around with Top command and wanted to see if there is a way to log only the top 15 process. When logging in batch mode.... The output is very long, I just want the first 22 lines to be logged.

```
top -b -d 60 >topLog.txt
```

Will log the top output every minute... but will log everything.

I tried different combinations with head command...

```
top -b -d 60 | head -22 >topLog.txt
```

```
top -d 60 | head -22 >topLog.txt
```

The first command gave me the output I was looking for... but did not repeat every minute as I was hoping.

The second command didn't work at all.. as the output was messed up.

I am still relatively new to using CLI commands and may be combining them wrong, If anyone has any tips on how to get what I'm Looking for, please let me know. Thanks Ahead.

---

