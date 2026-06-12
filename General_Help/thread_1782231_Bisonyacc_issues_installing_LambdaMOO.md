---
title: "Bison/yacc issues installing LambdaMOO"
date: 2011-06-14
forum: General Help
---

### Post by musendrophilus on 2011-06-14
```

sudo make
yacc -d parser.y 
/usr/bin/bison: cannot open file `y.tab.c': Permission denied
make: *** [parser.c] Error 1

```

So while running make for LambdaMOO-1.8.1 I got this error. AFAIK Bison has the same functionality as yacc. Do I have to change the permissions on y.tab.c or do I have to create the file y.tab.c?

---

