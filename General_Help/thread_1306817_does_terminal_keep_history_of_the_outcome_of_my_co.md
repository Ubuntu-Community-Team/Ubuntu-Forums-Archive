---
title: "does terminal keep history of the outcome of my commands?"
date: 2009-10-30
forum: General Help
---

### Post by chriskin on 2009-10-30
i Think i installed the .deb of IBM's office suite
but it might have failed , i never checked the outcome , had to leave the house.

does my terminal keep history of what happened after i pressed enter?

---

### Post by fragos on 2009-10-30
Yes -- until the terminal ap is closed.

---

### Post by SuperSonic4 on 2009-10-30
You can also pipe the output to a file

```
 command > file.txt
```

For example when I do it with pacman -Syu:

```
:: Synchronising package databases...
 kdemod-core is up to date
 kdemod-extragear is up to date
 kdemod-playground is up to date
 core is up to date
 extra is up to date
 community is up to date
 archlinuxfr is up to date
:: Starting full system upgrade...
 local database is up to date

```

(the attached is the same)

---

### Post by chriskin on 2009-10-30
> **fragos said:**
> Yes -- until the terminal ap is closed.

even if this won't help me now, can you tell me what you mean (other than the obvious "look at the screen" i hope) on checking the outcome history , for later use?

---

### Post by phillw on 2009-10-30
> **chriskin said:**
> i Think i installed the .deb of IBM's office suite
but it might have failed , i never checked the outcome , had to leave the house.

does my terminal keep history of what happened after i pressed enter?


```
dpkg-query -l *what_ever_the_module_is_called*
```

Include the * at the start and end - that will give you some information on the package, post back what you get.

Phill.

---

### Post by chriskin on 2009-10-30
> **phillw said:**
> ```
dpkg-query -l *what_ever_the_module_is_called*
```

Include the * at the start and end - that will give you some information on the package, post back what you get.

Phill.

the thing i was doing is gone now , i want to know for later use

---

### Post by shaggy999 on 2009-10-30
The terminal by default only remembers back maybe a few hundred lines of output and only while that session is open. To scroll up through your text you want to type SHIFT + PGUP and SHIFT + PGDWN.

If you want to know what commands have been run then you are interested in the history command. You can find out more about it by typing 'man history'

---

### Post by chriskin on 2009-10-30
> **shaggy999 said:**
> The terminal by default only remembers back maybe a few hundred lines of output and only while that session is open. To scroll up through your text you want to type SHIFT + PGUP and SHIFT + PGDWN.

If you want to know what commands have been run then you are interested in the history command. You can find out more about it by typing 'man history'
thanks, even though the second part is not what i asked for

---

### Post by fragos on 2009-10-30
Information provided on the command line frequently does a better job of error reporting but the system logs do offer insight into problems as well. @Supersonic4 did offer a workable solution with "command > file.txt". If all else fails does re-initiate from the command line as Supersonic4 suggested. Not what you asked for but perhaps the only way to get at the problem.

---

