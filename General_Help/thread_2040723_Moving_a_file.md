---
title: "Moving a file"
date: 2012-08-11
forum: General Help
---

### Post by wing0zero on 2012-08-11
First off hi to the community.

Im a new user of Ubuntu always been a Windows user but i guess i wanted somthing different/better for every day use, so far very nice, i have found all programs i use on Windows on here and replaced some with better programs iv'e found (still had to keep Win7 for gaming) but i have my first problem.

Iv'e installed Pidgen figured how to update it which was my first time using the Terminal, then i found a file to have Steam IM added to it.
Now the problem is simply putting the file in the folder, the file is called libsteam.so and the folder is /usr/lib/purple-2, i know i need some kind of root rights but see warnings about that and the whole sudo thing is confusing at the moment.

So can any advice is much appreciated, can i move the file using a command in the Terminal?

Thanx in advance.

---

### Post by CatKiller on 2012-08-11
As a novice, you're less likely to do something by mistake with ```
gksudo nautilus
```

---

### Post by ads52 on 2012-08-12
> **wing0zero said:**
> So can any advice is much appreciated, can i move the file using a command in the Terminal?

As CatKiller has pointed out there is some risk in using the Terminal for moving files particulary using *sudo*, Linux often has not much of a safety catch and will  allow you to shoot yourself in the foot with little or no warning :).

Mind you opening nautilus with gksudo has risk as well, if you are a little unsure of exactly what you are doing. Can I suggest a little careful reading up on the usage of the 2 terminal commands you might be using? These are *mv* (which will move or rename files) and *ln* (which makes links between files). 

Is there a guide that you are following that asks for this file to moved in the way you suggest?

---

