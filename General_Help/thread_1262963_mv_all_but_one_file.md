---
title: "mv all but one file"
date: 2009-09-10
forum: General Help
---

### Post by gypsumwolf on 2009-09-10
Is there a way to mv all folders and files minus 1 file?

Ex.) mv * -except foo.tar

---

### Post by sisco311 on 2009-09-10
try something like:
```
ls | grep -x -v "file name" | xargs -I {} mv {} /dest/dir
```

---

### Post by stylishpants on 2009-09-10
In bash:

```

mv !(foo.tar) <destination>
```

For more information:

```
man bash | less -p "\!\(pattern-list)"
```

---

