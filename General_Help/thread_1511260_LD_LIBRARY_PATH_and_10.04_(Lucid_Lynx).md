---
title: "LD_LIBRARY_PATH and 10.04 (Lucid Lynx)"
date: 2010-06-16
forum: General Help
---

### Post by Emanuele_Z on 2010-06-16
Hi guys,

I usually develop in Ubuntu, and use LD_LIBRARY_PATH override to let mplayer use my own dev version of libav*.so.
What I usually do is:
```

export LD_LIBRARY_PATH=<path where my so are>

```
Then, if I execute
```

ldd `which mplayer`

```
It will show me that for libav*.so is loading the ones inside *<path where my so are>*.

But with 10.04 now I can't do this any more.
Is this expected?
Why can't I find anything about it nowhere?

How can I deal with this behaviour in 10.04?

Thanks again,
Cheers,

---

### Post by bodhi.zazen on 2010-06-16
Moved to general help.

---

