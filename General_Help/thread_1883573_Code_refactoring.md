---
title: "Code refactoring"
date: 2011-11-19
forum: General Help
---

### Post by radu992 on 2011-11-19
I have to make a refactoring to some sources from a folder. To do that I have to insert on the first line of all the sources files a text and then I have to delete all the spaces and the tabs at the and of the lines. Can you help me? If you do you would really help me a lot.:)

---

### Post by WasMeHere on 2011-11-19
Hi radu992,

You can use ***cat*** to add the first line, something like this
```
cat first-line.c file1-orig.c > file1-new.c
```
and you can use ***sed*** to delete whitespace from the end of line. Find some tutorial about sed on the internet! I think it will be useful for you several times.

Have fun finding out
Olle

---

