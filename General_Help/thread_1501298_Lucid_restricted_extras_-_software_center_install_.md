---
title: "Lucid restricted extras - software center install fails"
date: 2010-06-04
forum: General Help
---

### Post by charonred on 2010-06-04
I have this same problem on a PC and a new Notebook - when using Software Centre to install 'Ubuntu Restricted Extras' it gets to 87% and then no further, regardless how long you leave it running. 

So you give up waiting after an hour or so, and it still won't play DVDs - it just gives an error message.

If you try to un-install it, you get the message that it didn't install properly or complete, and that it must be fixed before it can be un-installed or installed.

So what's broken, and how do I fix it.

.

---

### Post by mikewhatever on 2010-06-04
Try running the following command in Applications->Accessories->Terminal:
```
sudo apt-get install -f
```
It will try to fix broken and partially installed packages.

---

### Post by charonred on 2010-06-04
thanks, tried that, but all it prompted was for me to auto remove the original Linux headers for Lucid

---

### Post by oldos2er on 2010-06-04
I don't use Software Center, but does it show you which package it's failing on? Have you tried running ```
sudo dpkg --configure -a
``` ?

To play encrypted DVDs, see [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by bigsmitty64 on 2010-06-04
Try it through synaptic.

---

### Post by charonred on 2010-06-04
I fixed it by entering these 2 scripts

```
sudo apt-get remove --purge ubuntu-restricted-extras
```

```
sudo apt-get install ubuntu-restricted-extras
```

took a hour or so on the Gigabyte desktop (seemed to uninstall all MS core fonts ?), but only took a minute on the Asus K52F notebook

.

---

