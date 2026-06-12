---
title: "DarkIce"
date: 2006-04-01
forum: General Help
---

### Post by sprinkles on 2006-04-01
I'm trying to set up DarkIce for streaming (one of the two reasons I can't switch 100% ubuntu).

I compiled it OK, but when I try to run it I get the error:
```
DarkIce: DarkIce.cpp:215: DarkIce not compiled with lame support, thus can't con nect to IceCast 1.x, stream: icecast-0 [0]
```

I looked in the log for the install, and it finds lame:
```
configure:5972: checking for lame library at /usr 
configure:6010: result: found at /usr 
```

Does anyone know why it won't work?

---

### Post by _aeon on 2006-04-01
You need lame libs. Try install liblame0 and liblame-dev (search in Synaptic) and compile again.

Ah, and you probably need to add --with-lame-prefix=/usr/local/lib in the configure script ;)

---

