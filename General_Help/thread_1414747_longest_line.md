---
title: "longest line"
date: 2010-02-24
forum: General Help
---

### Post by learningUbunt on 2010-02-24
how would you print out the length of the longest line in a file?

---

### Post by michy99 on 2010-02-24
Are these homework questions by any chance?

---

### Post by learningUbunt on 2010-02-24
Def. not homework, I'm much too old for Homework. I'm just trying to learn about Ubuntu/linux.

Ubuntu classes exist?

---

### Post by kaibob on 2010-02-24
It's common to see new forum members with only a few posts ask questions that would appear to be school work. For example, 

[http://ubuntuforums.org/showthread.php?t=1414661](http://ubuntuforums.org/showthread.php?t=1414661)

To answer your question, the wc command will do what you want:

```
wc -L file
```

See the wc man page for more information.

---

### Post by gmargo on 2010-02-24
That wc -L is sweet.  Here's what came to my mind (more commands to learn!)
```

cat filename | awk '{ print length() }' | sort -rn | head -1

```

---

