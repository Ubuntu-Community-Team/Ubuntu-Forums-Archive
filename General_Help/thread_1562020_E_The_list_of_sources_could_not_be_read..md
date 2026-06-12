---
title: "E: The list of sources could not be read."
date: 2010-08-27
forum: General Help
---

### Post by siteregsam on 2010-08-27
Hi,

  I had installed ubuntu 10.04 and tried to update, got following problem

[I]sam@sam-laptop:~$ sudo apt-get install update
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/bisigi-ppa-lucid.list
E: The list of sources could not be read.[/I]

How to overcome this?

---

### Post by plucky on 2010-08-27
> **siteregsam said:**
> Hi,

  I had installed ubuntu 10.04 and tried to update, got following problem

[I]sam@sam-laptop:~$ sudo apt-get install update
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/bisigi-ppa-lucid.list
E: The list of sources could not be read.[/I]

How to overcome this?

From a terminal post output of ```
cat /etc/apt/sources.list.d/bisigi-ppa-lucid.list
```

There is something in line 2 that it doesn't like.

To edit the file use ```
gksudo gedit /etc/apt/sources.list.d/bisigi-ppa-lucid.list
``` and remove whatever looks out of place.

If no luck,post the output of the "cat" command so we can take a look.

Good Luck

---

### Post by siteregsam on 2010-08-30
Thanks plucky....

---

### Post by zerin on 2010-09-01
Thanks man! all i had to do was delete the "n" at line two and it was solved.

---

### Post by Eskobar on 2010-11-13
Appreciate it Plucky!!!!!  I was pulling the little hair that I have left....OUT!

---

