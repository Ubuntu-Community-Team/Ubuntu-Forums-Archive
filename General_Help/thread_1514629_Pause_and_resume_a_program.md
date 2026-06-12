---
title: "Pause and resume a program?"
date: 2010-06-21
forum: General Help
---

### Post by benjorino on 2010-06-21
Hi,

I am wondering if there exists a way to pause and resume a program, in a manner a little like the way 'hibernate' works.

I know a way to do this where the program remains in RAM, but I would like to save it to disk.

So essentially what I want to do is:

1. Run program
2. Pause program
3. Copy entire program state from RAM to Hard disk
4. Resume program at a later date, perhaps after shutdowns etc.

Is this possible?

Many thanks,
Ben

---

### Post by amauk on 2010-06-21
[http://code.google.com/p/cryopid/](http://code.google.com/p/cryopid/)

Although it's not seen any updates since March this year, and it seems to be broken at the moment due to a recent kernel overhaul of how processes are handled

---

### Post by MooPi on 2010-06-21
I don't know personally but it would help the community if you listed the program you wish to attempt this on.

---

### Post by benjorino on 2010-06-21
> **MooPi said:**
> I don't know personally but it would help the community if you listed the program you wish to attempt this on.

Its for a computer simulation which I have written myself.
It is written in C, and compiled to a single file.

---

### Post by benjorino on 2010-06-21
> **amauk said:**
> [http://code.google.com/p/cryopid/](http://code.google.com/p/cryopid/)

Although it's not seen any updates since March this year, and it seems to be broken at the moment due to a recent kernel overhaul of how processes are handled

That's exactly the sort of functionality I need, however I run this code on a computer on which I do not have permission to add and remove programs... I was wondering if there was a way to use the built-in functionality of Linux to achieve this?

---

### Post by happyhamster on 2010-06-21
Another try is to run your job in a virtual machine (if available on that computer). Or perhaps rewrite your program to initialize it's variables from a file, and also store those values to file when stopping the program.

---

