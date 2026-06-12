---
title: "synaptic manager error message"
date: 2009-07-11
forum: General Help
---

### Post by genibag on 2009-07-11
[SIZE=2]hello everybody, i'm new with ubutu. i installed ubutu 8.04 , everything was fine until i tried to install LimeWire 5.1.4. with the GDebi Package installer. when it was (i think ) downloding something extra for the limewire it freeze.(stop downloading, installing)
i tried to reistall again but with the same way and says only one managment tool is allowed .....

i tryed again to find it through synaptic package manager but an error message appear :

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

im new and i really don't know how to use (don't know) any command for the terminal. any help.
[/SIZE]

---

### Post by drs305 on 2009-07-11
Hi genibag, welcome to the Ubuntu forums!

Type this in a terminal (Applications, Accessories, Terminal):
```

sudo dpkg --configure -a

```

You will be asked for your password. You won't see what you type. Hit ENTER after you have typed your password.

Ubuntu only allows one installer to run at a time so it doesn't get 'confused'. So you can't have gdebi and synaptic operating at the same time.

---

### Post by genibag on 2009-07-11
thanks for your help

---

