---
title: "Make xgamma settings permanent?"
date: 2012-07-29
forum: General Help
---

### Post by Matt12334 on 2012-07-29
I have tried creating the startup command "xgamma -gamma .8". This works for about .3 seconds whenever I login, but it immediately reverts back to 1.0, even though the command "xgamma" tells me that all of my gamma values are .8.  Entering the command again returns the gamma to what it would be.

Is there some way I can make my xgamma settings permanent without having to enter it every single time?

---

### Post by Matt12334 on 2012-07-29
Alright, I figured it out myself.  I created the following script:
```

&#65279;#! /bin/sh
sleep 1
xgamma -gamma .8

```and named it xgammaboot.sh (not that the name matters).  I then added it to my home folder as a hidden file and added it to my startup programs.  Worked like a charm!  If anybody else tries this, it may be necessary for you to set the sleep time to a different value, but 1 second was enough for me.  

Let me know if this works for you as well. :p

---

### Post by ronnotramper on 2012-09-19
Yes. It works for me too.
Thanks, Ronno

---

