---
title: "How do I turn thumbnail caching off?"
date: 2006-03-25
forum: General Help
---

### Post by JamesNorris on 2006-03-25
I want to be able to view thumbnails of images and stuff in konq. But I don't like how it caches every one of them in the ~/.Thumbnails folder. 

Is there a way of turning the caching off, without losing the ability to preview files with a thumbnail in konq?

---

### Post by JamesNorris on 2006-03-30
erm... Bump??

---

### Post by GeneralZod on 2006-03-30
Dunno :) Try asking on IRC:

#kde on freenode.irc.net

Good luck,
Simon

---

### Post by JamesNorris on 2006-04-02
[QUOTE=GeneralZod]Dunno :) Try asking on IRC:

#kde on freenode.irc.net

Good luck,
Simon[/QUOTE]

lol, thanks, buyt this didn't work, #kde is dead, aside from other clueless souls like me after help. Nobody could answer my question...

---

### Post by alcosmurf on 2006-04-27
I had the same problem so i just chmoded the .thumbnails folder with no privileges (so nothing could be written to it).
```
chmod a-rwX ~/.thumbnails/
```
Not the best fix but it sorted it for me :D

---

