---
title: "Make all"
date: 2010-10-17
forum: General Help
---

### Post by teppel on 2010-10-17
Hi all,

I was looking through some of the makefile tutorials and i still don get it how it work.

Let say i have a a.cpp inside a folder located at the desktop

content inside the folder :
a.cpp - contain all my program code
Makefile.txt

**content inside makefile.txt**
all: g++ a.cpp -o a

execute in terminal > make all

At the terminal i execute the make all command it keep showing
make: *** No rule to make target `all'.  Stop.

---

### Post by teppel on 2010-10-17
up for help

---

### Post by gmargo on 2010-10-17
It's the name of your makefile.

If you read the **make(1)** man page, you'll see that, without a **-f** option, **make** will search for a makefile with one of three names, in this order:  GNUmakefile, makefile, Makefile.  It is recommended that you not use the first, but instead use "makefile" or "Makefile" (with no .txt file extension.)

```

all: a

a: a.cpp
        g++ -o a a.cpp

```
Don't forget that the whitespace before the "g++" must be a tab, not spaces.

---

