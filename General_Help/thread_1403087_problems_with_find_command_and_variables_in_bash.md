---
title: "problems with find command and variables in bash"
date: 2010-02-09
forum: General Help
---

### Post by mohaakilla51 on 2010-02-09
ok, so if I run
```
find . -path 'abc' -not -path '*xyz'
```
Everything functions as I expect it to.
But if I put everything after the -not into a variable and run
```
find . -path 'abc' $VARIABLE
```
it doesn't function properly.

Any help here?

---

### Post by Brandon Williams on 2010-02-09
Are there quotes around *xyz in the variable value? They would probably not be interpretted correctly by the shell if they are in the variable's value. In other words, you should assign to the variable like this:
```
VARIABLE='-not -path *xyz'
```
not like this
```
VARIABLE="-not -path '*xyz'"
```

---

