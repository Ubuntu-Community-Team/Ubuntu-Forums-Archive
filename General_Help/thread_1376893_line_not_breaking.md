---
title: "line not breaking"
date: 2010-01-09
forum: General Help
---

### Post by jusitndm on 2010-01-09
Hi
This is my first forum post  but I really think i need help this time.
The problem is:
after i typed: cat </dev/urandom (i think it inserted a controll character where i cant find it)
At my bash prompt (sh and python are fine) and only once per prompt before the line should break it just starts at the beginning of the same line and overwrites itsself (only on the screen its interpreted as typed) .
This really bugs me because i love working with bash and i don't want to reinstall the system.
I tryed reinstalling bash and readline  without success.
is there any config files i could check? 
my PS1=\e[44m\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ \e[0m

---

### Post by dcstar on 2010-01-10
> **jusitndm said:**
> Hi
This is my first forum post  but I really think i need help this time.
The problem is:
after i typed: cat </dev/urandom (i think it inserted a controll character where i cant find it)
At my bash prompt (sh and python are fine) and only once per prompt before the line should break it just starts at the beginning of the same line and overwrites itsself (only on the screen its interpreted as typed) .
This really bugs me because i love working with bash and i don't want to reinstall the system.
I tryed reinstalling bash and readline  without success.
is there any config files i could check? 
my PS1=\e[44m\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ \e[0m

Here is my 9.10 PS1 (which I assume is default), if you have changed yours to something different then there is little anyone else can do:
```
PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

---

### Post by jusitndm on 2010-01-10
Changing my prompt back to default fixed it, thanks.
Does anyone have a clue why?

---

### Post by dcstar on 2010-01-12
> **jusitndm said:**
> Changing my prompt back to default fixed it, thanks.
Does anyone have a clue why?

Because you put in some bogus escape code that broke it?

---

