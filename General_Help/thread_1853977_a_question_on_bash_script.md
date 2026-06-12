---
title: "a question on bash script"
date: 2011-10-03
forum: General Help
---

### Post by volvolinux on 2011-10-03
Dear,
 
I have find some scripts is preferred to put a placeholder : before assign value to parameters, Do you know why they want to do this?
 
like:
 
: ${CONFIG:=/proc/config.gz}
 
but actually, ${CONFIG:=/proc/config.gz} does the same thing.
 
any idea?
 
THanks.

---

### Post by sisco311 on 2011-10-03
[noparse]The parameter expansion (${parameter:=word}) is passed as an argument to the null command (:) in order to prevent bash from interpreting the result of the expansion as a command:[/noparse]

```
[sisco@acme xtmp]$ foo=
[sisco@acme xtmp]$ ${foo:=bar}
[color=red]bash: bar: command not found[/color]
[sisco@acme xtmp]$ foo=
[sisco@acme xtmp]$ : ${foo:=bar}
[sisco@acme xtmp]$ 

```

---

