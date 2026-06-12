---
title: "Not allowing all files in a folder to execute as a program?"
date: 2010-08-08
forum: General Help
---

### Post by janoochen on 2010-08-08
I want to "untick" Allow to execute as a program.

I know I can use chmod but not sure about the right argument

Any suggestions?

---

### Post by jbrown96 on 2010-08-08
```
chmod ugo-x FILE
```

---

### Post by janoochen on 2010-08-08
Thanks, but how can I do it for all the files in a folder?

---

### Post by WorMzy on 2010-08-08
```
chmod ugo-x *.*
```

Will remove executable permissions on EVERYTHING in a folder that has a "." in it's name, including folders. You'll need to manually "chmod +x" any affected folders afterwards.

```
chmod ugo-x *.txt
```

Will do the same, but just for .txt files.

I'm sure you get the idea. Just use wildcards (the asterisks) to create a pattern that will do what you want.

---

### Post by janoochen on 2010-08-08
Thanks! I love xkcd too.

---

