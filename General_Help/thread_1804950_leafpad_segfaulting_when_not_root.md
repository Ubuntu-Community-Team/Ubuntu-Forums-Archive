---
title: "leafpad segfaulting when not root"
date: 2011-07-15
forum: General Help
---

### Post by dijxtra on 2011-07-15
I've been happily using jaunty until yesterday. After reinstalling kubuntu to natty everything works fine except leafpad:

nick@rilmir:~$ sudo leafpad
[sudo] password for nick: 
nick@rilmir:~$ leafpad
Segmentation fault
nick@rilmir:~$ 

So, when I run it as root, it works, but when I run it as ordinary user, it segfaults.

Where do I even start looking?

---

### Post by andrewthomas on 2011-07-15
maybe try and delete the leafpadrc file

```
rm ~/.config/leafpad/leafpadrc
```

for the user that leafpad does not work for.

---

