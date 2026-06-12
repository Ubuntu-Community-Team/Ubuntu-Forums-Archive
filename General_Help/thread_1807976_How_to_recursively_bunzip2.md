---
title: "How to recursively bunzip2"
date: 2011-07-19
forum: General Help
---

### Post by Alistair George on 2011-07-19
Hi since there is no directory recursive option for bunzip2, any ideas on how to do this as I have lots of .bz2 files scattered throughout from an unknown archive program.
Thanks vm.
Alistair.

---

### Post by AlphaLexman on 2011-07-19
You could use '**find**' with the action '**-exec**' option.
```
find . -name "*.bz2" -execdir bunzip2 {} +
```

---

### Post by Alistair George on 2011-07-19
> **AlphaLexman said:**
> You could use '**find**' with the action '**-exec**' option.
```
find . -name "*.bz2" -execdir bunzip2 {} +
```

Brilliant - was lovely to watch all the subdir .bz2 icons change into the real thing!

Code should be wrapped in an executable; as there is nothing I could find that would do this and many dont have the clues you have friend thanks vm.
Alistair.

---

### Post by Morpholinux on 2011-09-05
I know it is solved, but maybe you will like more something like>

bunzip2 `find -name "*bz2"`

---

