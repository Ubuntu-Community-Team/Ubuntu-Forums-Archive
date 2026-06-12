---
title: "Xmacro and fortune"
date: 2009-09-01
forum: General Help
---

### Post by bob2098 on 2009-09-01
Is there a way to add a string before the output of a file when piping it into another command.

I want to have xmacroplay to type out the output of fortune so essentially:

String 'output of fortune'

---

### Post by DaithiF on 2009-09-01
```
echo "string '$(fortune)'" | someprogram
```
$(<command>) in bash runs the command, similar (but generally preferred) to enclosing a command in backticks ``

---

