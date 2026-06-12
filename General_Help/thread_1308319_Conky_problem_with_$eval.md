---
title: "Conky problem with $eval"
date: 2009-10-31
forum: General Help
---

### Post by leonbadman on 2009-10-31
Hi, 

in my conky config I've:

${eval ${exec php script.php param1 param2}}

the script.php is something like

echo '{$color 0000FF} Hi !!!';

The output in conky is:

{$color 0000FF} Hi !!!

What's wrong?

TIA
Ciao
Leonardo Cosmai

---

### Post by Brandon Williams on 2009-11-01
Try this instead:
```
${execp php script.php param1 param2}
```

The difference between exec and execp is that execp will parse the output as conky variables and formatting commands.

---

### Post by leonbadman on 2009-11-02
Thanx. The problem seems to exist only in the new 1.7.2; with 1.7.1.1 no problem.

Now the problem is the buffer for $eval: to small, only 256 char.

Thanx
Ciao
Leonardo Cosmai

---

