---
title: "Google Earth won't start"
date: 2010-03-13
forum: General Help
---

### Post by tombaugh on 2010-03-13
Hi,

When I'm trying to start Google Earth, I get

```
googleearth-bin: malloc.c:3074: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted
```Here's someone who had the same problem but I'm not experienced enough to use the information in that thread: [http://bbs.archlinux.org/viewtopic.php?pid=654908](http://bbs.archlinux.org/viewtopic.php?pid=654908)

Thanks!

---

### Post by scouser73 on 2010-03-13
Now this is just a suggestion, but you could delete the folder called **.googleearth** from the home folder.  The folder **.googleearth** is hidden, so press **Ctrl & H** to un-hide it & then delete the folder.  Now click on Google Earth and see if it rectifies the problem.

---

### Post by tombaugh on 2010-03-14
I've got no such folder here...

---

### Post by Tikkyca on 2010-03-14
Happened one time to me,i just restarted my pc and everthing was working okay.

---

### Post by malangaman on 2010-06-01
Worked most excellently for me.
I had to delete .googleearth folder in home folder left over from previous install:
Places->Home Folder->View->Show Hidden Files.

---

### Post by felixq78 on 2011-04-20
> **tombaugh said:**
> I've got no such folder here...

Yeah! Me neither! Where does he mean?

---

