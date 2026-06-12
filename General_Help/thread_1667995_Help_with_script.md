---
title: "Help with script"
date: 2011-01-15
forum: General Help
---

### Post by sn0m on 2011-01-15
Hi Guys
This is probably very easy for some of you.
I'm trying to understand the following script and use it in my backup.sh script but getting stuck at the special character thing.
I'd appreciate if one of you could spare a few minutes and explain to me what all "^[^ ]* section mean....

if grep -q "^[^ ]* ${TESTDIR} " /etc/mtab; then
        echo mounted
else
        echo not mounted
fi

Thanx for your help in advance

Sokol

---

### Post by Girya on 2011-01-15
> **sn0m said:**
> Hi Guys
This is probably very easy for some of you.
I'm trying to understand the following script and use it in my backup.sh script but getting stuck at the special character thing.
I'd appreciate if one of you could spare a few minutes and explain to me what all "^[^ ]* section mean....

if grep -q "^[^ ]* ${TESTDIR} " /etc/mtab; then
        echo mounted
else
        echo not mounted
fi

Thanx for your help in advance

Sokol

I'll take a stab at it > ^[^ ]* means a line that doesn't begin with a space. 

^ = beginning of a line
[^ ] = no space 
* wildcard any character

---

### Post by sisco311 on 2011-01-15
"^[^ ]* ${TESTDIR} "

The first ^ matches the empty string at the beginning of a line
[^ ] matches any character but a space
* matches the preceding item zero or more times
the rest is trivial.

Something like "* ${TESTDIR} " or "^* ${TESTDIR} " will not match anything in a basic or Perl regular expression, because * matches the _preceding_ character which doesn't exist.

"^.* ${TESTDIR} " will also work, but "^[^ ]* ${TESTDIR} " is more efficient because the parsing stops if the first character is a space (the line is probably empty).   

See:
```
man grep | less +/"REGULAR EXPRESSIONS"
```

---

### Post by sn0m on 2011-01-15
Thanx fella's you made my day. I've been googling ^ for a while with no luck.
I'm not a programmer, I'm a doctor and taking it slow to learn some stuff.
Thanx a lot guys
Sokol

---

