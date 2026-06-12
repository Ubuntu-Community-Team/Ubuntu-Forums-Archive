---
title: "Find out permissions of a directory"
date: 2011-06-30
forum: General Help
---

### Post by Externalist on 2011-06-30
Hi,

if I do ls -la on a file, it would show the permissions of the file on the left side.
I would like to do the same on a directory(ls -la directory) and have only one line printed out with the directory and it's permissions. But the result is the content of the directory and not the directory itself.
Is there a way to get around this issue?

Thanks! :)

---

### Post by nothingspecial on 2011-06-30
From the parent directory type 

```
ls -l
```

---

### Post by sisco311 on 2011-06-30
I think the OP is looking for the -d flag:
```
ls -ald file
```

---

### Post by nothingspecial on 2011-06-30
Is there any need for the -a flag?

---

### Post by sisco311 on 2011-06-30
> **nothingspecial said:**
> Is there any need for the -a flag?

Oops. I stand corrected, there is absolutely no need for -a. Thanks.

---

### Post by nothingspecial on 2011-06-30
:shock:

---

### Post by Externalist on 2011-06-30
That's awesome!
Exactly the answer I needed.
Thanks a bunch! :popcorn:

---

### Post by sisco311 on 2011-06-30
No problem!

---

