---
title: "Global Menu applet doesnt work!"
date: 2009-07-13
forum: General Help
---

### Post by joseacavallo on 2009-07-13
I see this applet in a webpage while looking for something else, i put the global menu key into the software source,  then i tried to install it, but it get stuck, and it shows me something like this:

Errors were encountered while processing:
 /var/cache/apt/archives/gnome-globalmenu-common_0.7.5-0ubuntu1~ppa1_all.deb
 /var/cache/apt/archives/gnome-globalmenu_0.7.5-0ubuntu1~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Im a little lost here, and i would really like to use this applet, any help is good...thanks.

---

### Post by shane2peru on 2009-07-13
For some reason it looks like your download got corrupted or something try this in a terminal (**Applications -> Accessories -> Terminal**)
```

sudo apt-get install -f

```
That should fix your errors then run this:

```

sudo apt-get clean

```
That will clean out your cache and remove the downloaded deb files

then:
```

sudo apt-get update && sudo apt-get upgrade

```
That will update and upgrade your system files, Then you should be able to install your file you were wanting to install.
Post any errors if you get them.

Shane

---

### Post by joseacavallo on 2009-07-14
Thanks man, it was what i needed!!!

---

