---
title: "Dissbale .pyc byte code from saving every time I run .py"
date: 2010-05-17
forum: General Help
---

### Post by StonedRaider on 2010-05-17
I am running ubuntu 9.10 and was wondering how to disable write access in python. I want to stop .pyc extensions from saving every time I run a .py file. Can anybody tell me how to do this?

Thanks, Tobin

---

### Post by mac9416 on 2010-05-17
Hi, StonedRaider,

In Python 2.6 you can use the -B option.

Just curious: why do you want to disable writing .pyc files?

---

### Post by StonedRaider on 2010-05-18
Does  -B work in python3.0? I want to disable because when I import a file it gets confused on which file to open .py or .pyc and doesn't open either

Thanks :)

---

### Post by mac9416 on 2010-05-18
I'm not sure if -B is available in 3.0. Install it and give it a try.  :)

It's strange that Python gets the .py and .pyc files confused. I would think it would always default to .pyc for speed and only go with .py files when it's been modified. Might be something to bring up on the Python forum since it could be a bug.

---

