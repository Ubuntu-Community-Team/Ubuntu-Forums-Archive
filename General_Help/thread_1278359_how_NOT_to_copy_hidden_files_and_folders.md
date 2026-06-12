---
title: "how NOT to copy hidden files and folders?"
date: 2009-09-29
forum: General Help
---

### Post by fduff on 2009-09-29
in a makefile, using ```
cp -r <src folder> <dest folder>
``` will also copy a whole bunch of hidden files and folders (.svn)

is there a simple way to avoid this and only copy 'visible' files/folders?
cheers.

---

### Post by diesch on 2009-09-29
```

find SRC_FOLDER/* -name '.*' -prune -o -print0 | xargs -i -0 cp --parents {} DEST_FOLDER

```

---

