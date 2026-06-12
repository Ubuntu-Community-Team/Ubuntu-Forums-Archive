---
title: "Problem with array in bash script"
date: 2010-11-27
forum: General Help
---

### Post by Mortesins93 on 2010-11-27
Hello,
I wanted to use arrays for my script but for some reason they don't work, here is my code:
```
#!/bin/bash
a=( 1 2 )
```and this is what I get if I execute it:
```
axel@axel-laptop:~$ sh prova
prova: 2: Syntax error: "(" unexpected
```The strange thing is that if I copy the same code directly on the terminal everything works fine. What should I do?

---

### Post by gmargo on 2010-11-27
**sh** is a link to the **dash** shell, not the **bash** shell.  **dash** does not support arrays.

You can run your "prova" script either by running bash directly or making the script executable.

```

$ bash prova

```  - or -
```

$ chmod +x prova
$ ./prova

```

---

### Post by Mortesins93 on 2010-12-02
Thank you so much, I tried it and it works great

---

