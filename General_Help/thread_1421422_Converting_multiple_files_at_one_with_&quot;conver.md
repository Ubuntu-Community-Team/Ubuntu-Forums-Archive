---
title: "Converting multiple files at one with &quot;convert&quot;"
date: 2010-03-04
forum: General Help
---

### Post by lordhaworth on 2010-03-04
Hi all,

I am converting .tif images to .eps and am trying to do a bunch of them at once. I have tried
```

convert *.tif *.eps

```

but this doesn't do it... Any suggestions?

Cheers

---

### Post by mcduck on 2010-03-04
Sure.

```
for file in *.tif; do convert "$file" "$file".eps; done
```

(the files will be named as "something.tif.eps" but they will be correct .eps files and you can just rename them to get rid of the "tif" part if you want to.)

---

### Post by lordhaworth on 2010-03-04
epic, cheers for the reply

---

