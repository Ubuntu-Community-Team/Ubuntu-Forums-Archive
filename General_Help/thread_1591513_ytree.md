---
title: "ytree"
date: 2010-10-09
forum: General Help
---

### Post by frank_n on 2010-10-09
This concerns file manager ytree for the text console, no graphic terminal.

The ytree version included in ubuntu 10.04 is 1.93-2 but the problem comes up
also with the current version 1.94 self-compiled without wide characters.

The problem is that the program does not even start. Message probably from
glib:


malloc.c:3096: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char
*) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct
malloc_chunk, fd)))) && old_size == 0) || ((unsigned long)
(old_size) >= (unsigned long)((((__builtin_offsetof (struct
malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 *
(sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned
long)old_end & pagemask) == 0)' failed. 


I have found a workaround but I cannot live with it. Would the concerned
Canonical maintaine rkindly look into it?

Thanks


frank

---

### Post by MichaelSammels on 2010-10-09
Hi. How did you install "ytree"?

```
sudo apt-get install ytree
```?

---

### Post by frank_n on 2010-10-09
I installed the packaged 1.93-2 from synaptics.

I have not installed the self-compiled 1.94, 
I run it (i.e. I try to run it) from its own directory.

Both bomb out with a malloc error.

---

### Post by frank_n on 2010-10-23
The newest version corrects the memory allocation error:

[http://www.han.de/~werner/ytree-1.96.tar.gz](http://www.han.de/~werner/ytree-1.96.tar.gz)

---

