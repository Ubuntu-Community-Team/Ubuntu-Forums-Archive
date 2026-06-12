---
title: "how to pause a list in terminal?"
date: 2011-09-22
forum: General Help
---

### Post by liquidmonkey on 2011-09-22
so i type something in terminal ('ls' or 'ifcopnfig') and the result will be a long list of things many 'terminal pages' long.

i would like to pause this list at each page length.

i remember it could be done in DOS back in 1980 but how about in terminal?

any ideas?
thanks!

---

### Post by dethorpe on 2011-09-22
Pipe it to less:
 
```
 
ls | less

```
 
"man less" for all the options.

---

### Post by nothingspecial on 2011-09-22
You could pipe it into less

eg
```

ls -R | less
```

That will allow you to scroll through the results and search the output.

See ```
man less
``` for details.


Edit: Ninjad :)

---

### Post by liquidmonkey on 2011-09-22
cool.

was hoping for a single letter though (i know that is very picky), like -p or something.

but thanks!

---

### Post by Lars Noodén on 2011-09-22
Your other option is to be fast enough hitting Ctrl-S

Piping is really the way to go in this.  It's easy once you get used to it.  Though on some keyboards the pipe symbol might not be the most convenient to get at.

---

### Post by drmrgd on 2011-09-22
Piping "less" or (my preference) "more" is definitely the way to go.  To make it faster for you, you could always add an alias to your .bashrc file so that something like 'lm' will result in a 'ls | more' call on a directory.

---

### Post by SoFl W on 2011-09-22
Press the "pause/break" key.

---

### Post by sisco311 on 2011-09-22
> **drmrgd said:**
> Piping "less" or (my preference) "more" is definitely the way to go.  To make it faster for you, you could always add an alias to your .bashrc file so that something like 'lm' will result in a 'ls | more' call on a directory.

I'd write a function:
```
lm ()
{
    ls --color "$@" | more
}
```

---

### Post by coldraven on 2011-09-22
I like to save the output to a file so that I can read it or compare results later.
For example to discover and save all your installed hardware to a text file.
```
sudo lshw > my_hardware.txt
```

---

