---
title: "Quick apt-get question"
date: 2010-02-26
forum: General Help
---

### Post by thecoffeeguy on 2010-02-26
Just a quick question as I re-familiarize myself with apt-get again...
So far, have had no luck finding what I am trying to do (back to the man page)

Basically, after doing a 'apt-get update' command, was it possible to see what packages have newer versions and can be upgraded?

For example, I am working with a system that has BASE 1.4.3 installed, and I know there is a newer version out (1.4.4), but want to make sure that is in the repository.

Does apt-get have something similar to portmaster in FreeBSD? Where it tells you what version you have installed, and what version is available to download?

Appreciate the help.

---

### Post by PoHandle on 2010-02-26
Try using```
apt-get -u upgrade
```

This should show you a list of packages to upgrade, and then give you a [Y/n] prompt to ask you whether you'd like to upgrade those packages.

---

