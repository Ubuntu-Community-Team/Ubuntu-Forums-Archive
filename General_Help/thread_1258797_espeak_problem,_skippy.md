---
title: "espeak problem, skippy"
date: 2009-09-05
forum: General Help
---

### Post by Cephi on 2009-09-05
Trying to use espeak, but it's very unreliable.  It skips parts of words, or whole words.  Give it the same command and once it will say it fine, the next time it'll skip the first half of the word -- even though it's the same exact command, one after another, nothing else about my system changing.

For example, if I give it:
```
while : ; do espeak "come on espeak" ; sleep .5 ; done
```

then it will say something like:
"come on espeak."
"come on espeak."
"eak."
"[just a quick clicking sound]"
"-n espeak."
"come on espeak."
"[just a quick clicking sound]"

etc.  I've tried using different speeds, with the -v option, but that doesn't change anything.  Any ideas?  Running jaunty here btw.

---

### Post by FFGANDALF on 2009-09-13
I've noticed this too. Depending on what you're doing you might want to use the -w option which outputs it to a wave file. I've noticed that it always pronounces every word when outputted as a wave file

---

