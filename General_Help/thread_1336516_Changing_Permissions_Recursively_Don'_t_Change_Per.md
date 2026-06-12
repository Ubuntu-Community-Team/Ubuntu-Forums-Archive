---
title: "Changing Permissions Recursively Don' t Change Permissions Recursively?"
date: 2009-11-24
forum: General Help
---

### Post by Blue Dolphins on 2009-11-24
When I try to change permissions recursively, it only affects folders, but not the files inside them.  This is the command I'm trying to use, what' s wrong with it?

Sudo chmod 775 -R /directory/

---

### Post by t0p on 2009-11-24
That command should work.  What's happening that you don't expect?

And why are you using *sudo*?

Oh yeah: *sudo* should not begin with a capital letter. ieit should be

```
sudo chmod 775 -R /directory/
```

not

```
Sudo chmod 775 -R /directory/
```

(if you should even be using *sudo*...)

---

