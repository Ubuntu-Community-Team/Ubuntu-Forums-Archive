---
title: "Cannot Install From Unauthenticated Sources?"
date: 2011-10-28
forum: General Help
---

### Post by fleamour on 2011-10-28
Cannot install various goodies from unauthenticated sources within 11.10's Ubuntu Software Centre...

I added the PPA, but the sources have no signed keys.

This solution does not work:

[http://ubuntuforums.org/showpost.php?p=8878470&postcount=3](http://ubuntuforums.org/showpost.php?p=8878470&postcount=3)

---

### Post by fleamour on 2011-10-29
```
sudo add-apt-repository ppa:user/ppa-name
```

```
sudo apt-get update
```

---

### Post by twtduck.ii on 2011-10-29
I got the same problem. I just installed Synaptic Package Manager from the Ubuntu Software Center and used that to update my "Unauthenticated" packages (ie. Wine 1.3 update).

---

