---
title: "Setting Environment Variables"
date: 2009-11-27
forum: General Help
---

### Post by Cerin on 2009-11-27
Sorry for the noob question, but I'm having trouble accessing an environment variable set in a script. It seems to set it correctly in the script, but I still can't access it from the shell. What am I doing wrong?

setvar.sh:
```
export THEVAR=1234
echo $THEVAR
```

```
[localhost]$ bash ./setvar.sh
1234
[localhost]$ echo $THEVAR

[localhost]$ 
```

---

### Post by scragar on 2009-11-27
```
. ./setvar.sh
echo $THEVAR
```
Run the code as a part to the current shell, or as a function.
```
setvar(){
  export THEVAR=1234
}
setvar
echo $THEVAR
```

---

### Post by Cerin on 2009-11-27
I want to be able to set environment variables by running a script, so other scripts have access to them, not manually typing them into a shell every time.

---

### Post by scragar on 2009-11-27
Then the first method works, just use```
. ./setvar.sh
```Instead of your current method, or could even try sourcing it.

---

### Post by Cerin on 2009-12-03
Sorry, I wasn't familiar with the . syntax. That works perfectly. Thanks!

---

