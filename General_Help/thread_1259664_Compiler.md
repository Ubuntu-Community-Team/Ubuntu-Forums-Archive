---
title: "Compiler"
date: 2009-09-06
forum: General Help
---

### Post by Hosmion on 2009-09-06
Hey everyone..  I was wondering if there was a program that could comprehend and run .bat programs that is a reliable, safe download.

Thanks you guys! :D :D :D

---

### Post by Liolikas on 2009-09-06
**dosbox** dos emulator.

---

### Post by dagoth_pie on 2009-09-06
ok, I may be barking up the wrong tree here, but .bat files are Dos Batch files aren't they, if so, first thing to try would be to download DosBox from the repository.

---

### Post by Hosmion on 2009-09-06
I made a file saying :

@echo off
echo Hi.

But, when I saved it to my desktop, it wouldn't open with it...

What should I do?

---

### Post by Barafu Albino Cheetah on 2009-09-06
.bat file is simply a shell script. Open it in text editor, see what it runs, and ask us about it. May be wine is OK, may be DosBox, may be virtualbox. 

Or you are asking about another .bat ?

---

### Post by Hosmion on 2009-09-06
How do I run it in Text Editor?

---

### Post by bear24rw on 2009-09-06
post the file

---

### Post by Hosmion on 2009-09-06
I attempted to upload the file but it says it is invalid.

---

### Post by phrostbyte on 2009-09-06
You must have Terminal open. (Accessories -> Terminal)


Try running your .bat file with wineconsole. Command:

```

wineconsole cmd

```

You can alternatively double click on a bat file and put in "wineconsole cmd" in how you want to execute it.

Or if you want, just convert it to a Bash script (which is more powerful then DOS scripts anyway).

```

#!/bin/bash

echo Hi.

```

Save that in a file script.sh and run it in the command line with ./script.sh

---

### Post by phrostbyte on 2009-09-06
And yes, I confirmed that wineconsole does in fact work to run .bat files. :)

Make sure you have [wine]("apt://wine") installed.

Launch this: wineconsole --backend=curses cmd

and you get a typical DOS command shell.

---

