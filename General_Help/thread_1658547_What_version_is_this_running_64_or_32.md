---
title: "What version is this running 64 or 32?"
date: 2011-01-02
forum: General Help
---

### Post by dgrafix on 2011-01-02
This is a 64 bit machine but i dont know what the OS is.

dan@dan-laptop:~$ uname -m
x86_64
dan@dan-laptop:~$ uname -r
2.6.32-25-generic
dan@dan-laptop:~$ 


It is a little confusing and i cannot seem to find anything on a simple test to see wether i am running 64 or 32 bit Ubuntu.

---

### Post by howefield on 2011-01-02
Try

```
 uname -a
```

If you still get x86_64 in the output, it is 64 bit.

---

### Post by dgrafix on 2011-01-02
ok.. gives:

Linux dan-laptop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux


Thanks

I guess it is defo 64 then? :)

---

### Post by IWantFroyo on 2011-01-02
That's it.

---

