---
title: "Create PGP Key"
date: 2012-02-21
forum: General Help
---

### Post by Orcris on 2012-02-21
How do I create a PGP key in Kubuntu? Most guides are for Ubuntu, which does this differently. I'm trying to create one for my Launchpad account.

---

### Post by jim_deadlock on 2012-02-21
If you use Thunderbird mail, get the Enigmail addon then you can generate a key pair via the OpenPGP menu.

... or:

gpg --gen-key

---

### Post by sudodus on 2012-02-21
+1 for gpg

I suggest that you learn about the command line syntax of ***gpg***. So read the built-in manual
```
man gpg
``` or browse for some tutorial on the internet.

Good luck :-)

---

### Post by oldos2er on 2012-02-21
You can use the GUI KDE app kgpg, [http://utils.kde.org/projects/kgpg/](http://utils.kde.org/projects/kgpg/)

---

