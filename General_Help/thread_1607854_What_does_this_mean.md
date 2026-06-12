---
title: "What does this mean?"
date: 2010-10-28
forum: General Help
---

### Post by squrl on 2010-10-28
I was expecting a new wav file. This is what I got back.I know the command works but not on this machine apparently. 

squrl@squrl-desktop:~$ timidity alleycat.mid -O -o alleycat.wav
Playmode `-' is not compiled in.

I'm using Timidity++2.13.2. It was installed from synaptic

---

### Post by 3Miro on 2010-10-28
This probably means that you entered the program parameters incorrectly. It is trying to play "-" or something.

Have you tried:
```
 timidity -O alleycat.mid -o alleycat.wav 
```
you will probably also get useful information if you type
```
 man timidity 
```

---

