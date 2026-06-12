---
title: "rdesktop muddles capslock state"
date: 2012-03-14
forum: General Help
---

### Post by bkline on 2012-03-14
I'm using rdesktop 1.7.0 on Ubuntu 11.10, and I've been plagued by a problem which causes random characters I type to come out capitalized, as if I had the caps lock key on.  Sometimes it's even so erratic that the state flips bAcK aNd fOrtH raNdoMLy while I'm typing.  Doesn't happen with any other apps, so I'm pretty confident it's not a hardware problem.  Anyone else experiencing this weirdness?

---

### Post by dino99 on 2012-03-14
looks like a borked .local config; delete it and log out/in, it will be recreated with the good settings

---

### Post by bkline on 2012-03-14
> **dino99 said:**
> looks like a borked .local config; delete it and log out/in, it will be recreated with the good settings

Thanks for the reply.  Not sure what file you're talking about.
```
$ ls -a ~ | grep local
.local
$ ls -R ~/.local | grep -i config
dictconfig.py
dictconfig.pyc
$ find ~/.local --name dictconfig.py
/home/bkline/.local/lib/python2.7/site-packages/django/utils/dictconfig.py
```

---

### Post by bkline on 2012-05-02
> **bkline said:**
> Thanks for the reply.  Not sure what file you're talking about.
```
$ ls -a ~ | grep local
.local
$ ls -R ~/.local | grep -i config
dictconfig.py
dictconfig.pyc
$ find ~/.local --name dictconfig.py
/home/bkline/.local/lib/python2.7/site-packages/django/utils/dictconfig.py
```

Can you give me a clue, please?  As shown by the output of my investigation, there don't appear to be any relevant files in the .local subtree on my system.

---

