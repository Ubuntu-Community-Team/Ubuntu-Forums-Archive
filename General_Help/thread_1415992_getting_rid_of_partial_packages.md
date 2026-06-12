---
title: "getting rid of partial packages"
date: 2010-02-25
forum: General Help
---

### Post by nischalinn on 2010-02-25
I've followed the instructions

sudo apt-get autoclean

then my terminal shows following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del google-chrome-beta 5.0.307.7-r38400 [12.8MB]
sarkar@sarkar-desktop:~$ 

now what to do,or is that all to do?

---

### Post by frigger908 on 2010-02-25
I believe thats all you do - but don't hang me on it as i'm not an expert.

---

### Post by pbrane on 2010-02-25
not sure what you mean by 'partial packages' but you can run
```

sudo apt-get autoremove

```
to remove unused packages. Packages that were dependencies for packages you removed.
I believe 'autoclean' just cleans the cached packages that were downloaded.

---

