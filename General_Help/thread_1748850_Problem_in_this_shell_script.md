---
title: "Problem in this shell script"
date: 2011-05-04
forum: General Help
---

### Post by kanishkdudeja on 2011-05-04
this is a shell script to add two numbers using a function.

```
function add
{
c=`expr $1 + $2`
echo $c
}
add 1 2

```

when i use it with sh add.sh it shows and error:
```

add.sh: 1: function: not found
expr: syntax error

add.sh: 6: add: not found

```

when i ran the same script in my lab which uses fedora..it run without any errors..

but not working in ubuntu 11.04.

---

### Post by papibe on 2011-05-04
Do you want to use bash? If so, you should run:
```
$ bash add.sh
```
I hope it helps.

---

### Post by kanishkdudeja on 2011-05-04
oh wow. thanks. it works now. but why not with sh?

---

### Post by ~Plue on 2011-05-04
> **kanishkdudeja said:**
> oh wow. thanks. it works now. but why not with sh?
Its being executed by dash, which is the default shell in debian/ubuntu (sh is a symlink to dash)
you could use a shebang to execute it with bash; just add to the beginning of the file,
```
#!/bin/bash
``` and run it from the command line without specifying the shell

Or to convert it to dash; replace *function add* with *add ()*

---

### Post by kanishkdudeja on 2011-05-04
oh..thanks a lot mate..:)

---

