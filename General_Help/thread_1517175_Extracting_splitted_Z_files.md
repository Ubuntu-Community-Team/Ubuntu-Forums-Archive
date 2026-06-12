---
title: "Extracting splitted Z files"
date: 2010-06-24
forum: General Help
---

### Post by forestG on 2010-06-24
Hi!

I have a bunch  of split  Z files and I want to extract them but I cannot find how. To be more specific I have a file named foo which is compressed into files foo.0Z, foo.1Z foo.2Z. I have tried uncompress but does not work I have tried gunzip,gzip etc but no result either. Even 7zip will not do the work. Any help would be much appreciated!!

---

### Post by gmargo on 2010-06-24
You should be able to concatenate them and uncompress them with something like:
```

cat foo.0Z foo.1Z foo.2Z | gzip -dc > foo

```

---

### Post by VH-BIL on 2010-06-24
Are you able to right click and select "Extract Here" on the first one?

---

### Post by forestG on 2010-06-25
> **VH-BIL said:**
> Are you able to right click and select "Extract Here" on the first one?
No, I have tried that. it does not work.

---

### Post by forestG on 2010-06-25
> **gmargo said:**
> You should be able to concatenate them and uncompress them with something like:
```

cat foo.0Z foo.1Z foo.2Z | gzip -dc > foo

```

I have tried that too but it does not work either. I finally did it with 7zip through windows. It is strange that the 7zip does not have the same functionality in Windows and Linux. And I do not mean the GUI but the actual decompressing abilities. 

Anyway, thanks for your time! I really appreciate it.

---

