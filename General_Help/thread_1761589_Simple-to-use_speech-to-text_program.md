---
title: "Simple-to-use speech-to-text program?"
date: 2011-05-18
forum: General Help
---

### Post by t0p on 2011-05-18
I've got a bunch of hand-written notes which I would like to put into **Kabikaboo** (great app by the way) - but it is a real pain reading stuff then typing it up.  I'd like a speech-to-text app, so I can just read my notes out loud and the computer will turn them into text files.

Looking through Synaptic, all I can find is **Julius**; and that does not seem to be an easy-to-use app at all.  So many parameters to set, an impenetratable (to me) manpage; and although I am a CLI user quite often, some kind of GUI would be nice.

Can anyone suggest an app?

---

### Post by StrayEddy on 2011-05-18
I found these apps, never tried any though:
 
**-Simon** alternative to Julius
[http://simon-listens.org/index.php?id=122&L=4](http://simon-listens.org/index.php?id=122&L=4)
 
**-Platypus**
 
-**Others**
[http://en.wikipedia.org/wiki/**Speech_recognition_in_Linux]("http://en.wikipedia.org/wiki/Speech_recognition_in_Linux")**

---

### Post by pqwoerituytrueiwoq on 2011-05-18
there is espeak 
```
~$ espeak "hello world"
```for a text file i would to this
```
cat /path/to/file.txt | espeak
```

---

### Post by t0p on 2011-05-18
> **StrayEddy said:**
> I found these apps, never tried any though:
 
**-Simon** alternative to Julius
[http://simon-listens.org/index.php?id=122&L=4](http://simon-listens.org/index.php?id=122&L=4)
 
**-Platypus**
 
-**Others**
[http://en.wikipedia.org/wiki/**Speech_recognition_in_Linux**]("http://en.wikipedia.org/wiki/Speech_recognition_in_Linux")

Thanks, I'll have a look at them.
> **pqwoerituytrueiwoq said:**
> there is espeak 
```
~$ espeak "hello world"
```for a text file i would to this
```
cat /path/to/file.txt | espeak
```

Yoy misunderstand.  I want a speech-to-text utility so I can read to my computer and it'll write it to a file.  **espeak** is a text-to-speech utility, that I can use to make my computer read me bed-time stories.  Speech-to-text, text-to-speech.  Not the same.

Oh, and there's a possibly quicker command to get espeak to read a text file:

```

espeak -f /path/to/file.txt

```

---

### Post by SynonM on 2011-05-19
Any success? 

:popcorn:

---

