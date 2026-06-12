---
title: "getdeb.com"
date: 2009-08-03
forum: General Help
---

### Post by nathang1392 on 2009-08-03
im sorry because i know this question is very dumb, but i just tried to install free basic from getdeb.com. everything installed fine, but when i go to look for it it isnt under programming. i cant find it anywhere. im so lost when it comes to things other than add/ remove programs.

---

### Post by TeoBigusGeekus on 2009-08-03
What package did you install?

---

### Post by Primefalcon on 2009-08-03
go to system => administration => synaptic 

and do a search for the program in there

---

### Post by tjwoosta on 2009-08-03
Try typing freebasic in a terminal. If that works you can make your own launcher.

---

### Post by wojox on 2009-08-03
Terminal:
```
whereis basic
```

---

### Post by rCXer on 2009-08-03
It's a compiler like gcc, so it won't appear on the menu. Typing...
```

which fbc

```
...in the terminal should tell you where the FreeBASIC compiler is.  On my computer it's in "/usr/local/bin/fbc".  To compile a file just use...
```

fbc file.bas

```

---

