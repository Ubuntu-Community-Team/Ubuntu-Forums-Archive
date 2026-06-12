---
title: "Not to see some files"
date: 2010-03-16
forum: General Help
---

### Post by andrejanubis on 2010-03-16
Hello all,
I know that with "ls *.pc" I can see all files end with ".pc", but how can I see all the other files, the one that don't end with ".pc"?
Thank you for all your help.

---

### Post by lotharmat on 2010-03-16
Just ls -I 

       ```
-I, --ignore=PATTERN
              do not list implied entries matching shell PATTERN
```

So in your case ls -I *.pc

---

### Post by geirha on 2010-03-16
With bash's extended globs, you can negate it like this:
```

shopt -s extglob
ls -d !(*.pc)

```

[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

---

### Post by lotharmat on 2010-03-16
You learn something new everyday!

---

### Post by andrejanubis on 2010-03-16
I miss that one, Thank you

---

