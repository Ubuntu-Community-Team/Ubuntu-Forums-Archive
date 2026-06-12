---
title: "Which kernel?"
date: 2005-03-05
forum: General Help
---

### Post by thorN on 2005-03-05
Hi,

I have an AMD Athlon XP 1900+ (Palomino core) processor and I'm running the k7 kernel (2.6.8.1-3-k7 to be precise).

However, when I run
```
$ uname -m
```
it says i686.

Does this mean I should use the 686 kernel instead?

I'm assuming trying it out will be painless, but I don't want to break anything.

---

### Post by kassetra on 2005-03-05
[QUOTE=thorN]Hi,

I have an AMD Athlon XP 1900+ (Palomino core) processor and I'm running the k7 kernel (2.6.8.1-3-k7 to be precise).

However, when I run
```
$ uname -m
```
it says i686.

Does this mean I should use the 686 kernel instead?

I'm assuming trying it out will be painless, but I don't want to break anything.[/QUOTE]

uname -m shows you the machine hardware name, as in, i386, i486, i586, i686, etc -- 
The kernel you're running is correct.  If you were running a first generation pentium chip, I'd say no, you need a different kernel.  Same goes for if you're running a 64-bit chip, you'd need a different kernel.  I guarantee if you were running the wrong kernel for your chip you'd know it very quickly.

So no worries!  You're good!  :)

---

### Post by thorN on 2005-03-06
ok, cheers.

Ive done a bit of reading up, I like how GNU can swap out such a large part of the system so efficiently.

If I change kernel, will this break programs 'make'ed with headers from this kernel?

---

### Post by kassetra on 2005-03-06
[QUOTE=thorN]If I change kernel, will this break programs 'make'ed with headers from this kernel?[/QUOTE]

Possibly, and it's also possible that it runs fine for a long time, and then you go to do something and it crashes.  If you're compiling code against a specific kernel's headers -- you're telling that program how that specific kernel works/operates... and if you change kernels, it's possible that the functions the program relied upon are different... make sense?

---

