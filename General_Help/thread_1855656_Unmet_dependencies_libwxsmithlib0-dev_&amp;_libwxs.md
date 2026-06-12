---
title: "Unmet dependencies? libwxsmithlib0-dev &amp; libwxsmithlib-dev?"
date: 2011-10-06
forum: General Help
---

### Post by cyiucsy on 2011-10-06
Hello all,

I am a happy Ubuntu user and I mainly use it for C/C++ programming.

Recently I have installed code:blocks and it's quite nice to use but then when I was trying to install Ubuntu updates, I got an error saying that

```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 codeblocks-contrib : Depends: codeblocks (= 10.05-1) but it is not going to be installed
 libwxsmithlib0-dev : Depends: libwxsmithlib-dev (= 10.05-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I have tried
```
sudo apt-get install -f
```
and
```
sudo apt-get remove codeblocks
```
but both returned with the same error messages.

It looks weird to me.
Any thoughts on solving this?

---

