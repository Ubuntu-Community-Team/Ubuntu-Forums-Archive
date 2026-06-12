---
title: "how printf works"
date: 2011-02-07
forum: General Help
---

### Post by Sunil Hari on 2011-02-07
please give me the technichal details of how printf works.I want to know the hardware details and translations that provides the conversion from code to display screen.pls reply me with source codes.

---

### Post by ahsan101 on 2011-02-07
Welcome to forums!!


Well Linux is absolutely free and its all about explore and research , all the functions are interconnected so there are a few chances someone will give you the detail... Better to google 
or download the source code and explore it yourself as its time-costly to explain such....

You can see this

[http://en.wikipedia.org/wiki/Printf_(Unix](http://en.wikipedia.org/wiki/Printf_(Unix))
[http://en.wikipedia.org/wiki/Printf](http://en.wikipedia.org/wiki/Printf)

I can find the best for you are these two!

---

### Post by Simian Man on 2011-02-07
printf just reads the format string and scans for the format codes.  When it finds one it reads an argument of the stack (or in a register according to the machine's convention).  It keeps going until a NUL in the format string.  It's pretty simple and has nothing to do with hardware.  See [http://en.wikipedia.org/wiki/Stdarg.h]("http://en.wikipedia.org/wiki/Stdarg.h") for more.

---

