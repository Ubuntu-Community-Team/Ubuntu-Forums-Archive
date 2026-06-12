---
title: "Bind Character to alt+key?"
date: 2009-12-23
forum: General Help
---

### Post by paal on 2009-12-23
In programming and various terminal programs (Screen, Vim) the [, ], { and } tends to be used a lot. I'm using a Norwegian keyboard where these are placed such that I have to stretch my fingers a bit too long for whats comfortable. To make it easier I though I'd try to make alt+[some key] be one of these characters. Is there a way that I can bind, say alt+æ (Norwegian letter) to '{' system wide?

Btw, is such thing called binding, mapping or something else? A bit confused by the terms... :)

---

### Post by PGScooter on 2009-12-26
hi paal,

I think you are correct that it is called a binding, as well as a mapping. I would suggest checking out ```
man xbindkeys
```. I wish I had step by step instructions but I've forgotten a lot.

Good luck!

---

### Post by rnerwein on 2009-12-26
hello
i use different keyboard for my boxes. and i am using xmodmap for the keyboard mapping. (man xmodmap). --> xmodmap -pke > mymodmap.txt, modify this texfileto your behavior of the maping .
then call: --> xmodmap mymodmap.txt
i did this in my profiles.
i hope this helps
ciao
   richi

---

