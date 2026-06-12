---
title: "Help with crafty use of cp command"
date: 2012-03-17
forum: General Help
---

### Post by jquis8411 on 2012-03-17
I have a problem only Ubuntu can solve. I am trying to figure out a way to copy files out of a directory tree. All the files that need to be copied  have the same prefix for example STRA.xxx but have a different extension for example STRA.98, STRA.97. However, I need to ignore or not copy files with a specific extension, for example .bar. man cp is great but I couldn't put together a command to this puzzler. Any help is great Thank you.

---

### Post by codemaniac on 2012-03-17
Something like that would help ?
```
find ~ -name "STRA*" -print | xargs  -I {} cp {} ~/test/
```

---

### Post by jquis8411 on 2012-03-17
Man, works like a charm. After I cd into the "test" directory  and rm *.bar  I have usable data. Thanks a million

---

### Post by codemaniac on 2012-03-17
EDIT :if you want to ignore some of the extensions, you may use some wild card expression that would find only the files with desired extension .
the below would find and copy only the files with extension 90 to 98 .
```
find ~ -name "STRA.9[0-8]" -print | xargs  -I {} cp {} ~/test
```

---

### Post by jquis8411 on 2012-03-17
The funny thing about how these files are created is that they are named numerically as they are produced foo.65,. foo.66 etc along with a .TGS which corresponds (foo.65.TGS, foo.66.TGS)  which are not needed by me. simply rm'ing the .TGS files from the output is easy enough and I get the data I need. Thanks again buddy

---

