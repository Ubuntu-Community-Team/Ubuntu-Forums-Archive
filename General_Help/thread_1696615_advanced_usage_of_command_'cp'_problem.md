---
title: "advanced usage of command 'cp' problem"
date: 2011-02-27
forum: General Help
---

### Post by -_-' on 2011-02-27
I copied a lot of files and some files aren't copied compleetly. So I´ve to copy again and replace them. The bad files are smaller than the good files I want to copy. Only the files which are bigger than their equivalent in the destionation folder must be copied (and has to overwrite the file). How can I do this?

---

### Post by quixote on 2011-02-28
Is there a reason why you don't want to use rsync?  That seems to me like what you need.  It'll ignore files that are identical on the target and only copy the ones that are different.  Type "man rsync" in a terminal for details.

---

### Post by seawolf167 on 2011-02-28
> **quixote said:**
> Is there a reason why you don't want to use rsync?

Aye, rsync is what I'd do

Something like

```
rsync -ruv /source /destination
```

The man page is full of all sorts of good info

```
man rsync
```

---

