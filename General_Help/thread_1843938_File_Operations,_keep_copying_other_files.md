---
title: "File Operations, keep copying other files?"
date: 2011-09-14
forum: General Help
---

### Post by Botruckle on 2011-09-14
(Ubuntu 11.04, Kernel 2.6.38-11, Gnome 2.32.1, classic interface)

Hi all,
I started copying a ton of files from one disk to another last night and expected that it would be done this morning when I got up. But instead, it had paused the copying process because it had trouble copying one file and was asking if I wanted to skip it or not. That seems like a bad approach.

Is there any way to have the system finish copying the rest of the files that it *can* copy while only asking about the files it can't? The way it is, I have to spend another hour waiting for it to copy files after telling it to skip.

---

### Post by SlugSlug on 2011-09-14
use rsync

rsync -a /files/to/copy /new/place

the -a is archive, it keeps permissions and stuff

---

### Post by seawolf167 on 2011-09-14
Aye, I'd suggest *rsync *as well

```
man rsync
```

```
rsync -ruva /source /destination
```

---

