---
title: "du command for only the current directories"
date: 2011-09-26
forum: General Help
---

### Post by mac4rfree on 2011-09-26
Hi guys,
 
I like to know the du command so that it gives the folder size for the current directories and not for the subdirectories.
 
Can somebody help me out with it..
 
Cheers!!!!

---

### Post by drmrgd on 2011-09-26
Try adding the -S option to the du command like this:

```
du -S
```

Also check out the man page for du to see other options that might give you what you want.  Just type "man du".

---

### Post by mac4rfree on 2011-09-27
@drmrgd,, ```
du -h --max-depth=1
``` this is what i was looking for.. :)
 
> **drmrgd said:**
> Try adding the -S option to the du command like this:
 
```
du -S
```
 
Also check out the man page for du to see other options that might give you what you want. Just type "man du".

---

