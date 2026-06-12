---
title: "Alias move files"
date: 2011-01-08
forum: General Help
---

### Post by ghostzen on 2011-01-08
Hi all,
I am testing the alias command, and I am stuck trying to create an alias that would move selected files to an existent directory I've already created.  
I have had success testing with:
alias say echo `date`
alias say echo hello world
 
but I am stuck with:

alias move mv ????? dir_test.  


I have no clue what should go in the ?????.  In bash, I would easily use "read xyz..." 

Thanks

---

### Post by sisco311 on 2011-01-08
Try:
```
alias move='mv -t dir'
```
or
write a function:
```
move () {
  move "$@" dir
}
```

See:
[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions)

---

### Post by ghostzen on 2011-01-09
Sweet!  Thank you, sisco311.  Btw, what does the -t mean?

---

### Post by AlphaLexman on 2011-01-09
> **ghostzen said:**
> Btw, what does the -t mean?

It means target directory.

See:

```
man mv
```

'man' is a manual for commands. It has lots of pages for all the commands on your system.

---

