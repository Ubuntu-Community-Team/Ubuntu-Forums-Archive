---
title: "64 bit mystery"
date: 2009-06-27
forum: General Help
---

### Post by papabill on 2009-06-27
Please pardon what may be a terribly stupid question, but how do I know if the machine I have is a 32bit or a 64bit?

---

### Post by philcamlin on 2009-06-27
what version did you install :D and download from the site

sudo apt-get install hardinfo

will tell you all you need to know

---

### Post by howefield on 2009-06-27
Open a terminal (Applications > Accessories > Terminal) and type

```
uname -a
```

What is returned ?

if it has x86_64 somewhere in the output, you have 64 bit.

---

### Post by fragos on 2009-06-28
All current Intel and AMD processors are 64 bit. However you need not run a 64 bit OS on them installing the Generic 32 bit Ubuntu may be your best bet so everything you might want to use will work. Some libraries are only available in 32 bit. Flash is one good example althogh it now may also be available in 64 bit.

---

### Post by MoreCowBell on 2009-06-30
Thanks, howefield.  That is just what I was looking for.  I have the 32-bit version installed.  My PC is capable of running at 64-bits, but I ran into compatibility problems with that distribution.  Thanks again.

Now, if only I can get my Web cam to work...

---

### Post by jerome1232 on 2009-06-30
One way to check for sure

```
grep --color lm /proc/cpuinfo
```

If you get a line of text with the letters lm highlighted your processor is 64 bit, if nothing returns it's 32 bit.

---

