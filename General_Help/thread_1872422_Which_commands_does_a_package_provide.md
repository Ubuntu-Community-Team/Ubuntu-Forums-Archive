---
title: "Which commands does a package provide ?"
date: 2011-10-30
forum: General Help
---

### Post by thyriel on 2011-10-30
Hi,

i hope its not a dumb question, but i cant find anyting about that. When i install a package, how can i find out which console commands it has added ?

For example, on my "Playground" Laptop im configuring a fresh Openbox installation. Beside others id need a package providing a sudo password box for X Server, so id thought about trying out the "libgksu2-0" package which has a very limited description.

So how do i figure out then the commands it provides ?

regards

---

### Post by dcstar on 2011-10-31
> **thyriel said:**
> Hi,

i hope its not a dumb question, but i cant find anyting about that. When i install a package, how can i find out which console commands it has added ?
.......

Synaptic will show you the installed files of all installed packages.

---

### Post by Lars Noodén on 2011-10-31
You can use [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html)

```

dpkg -L *packagename* | grep "bin/"

```

---

### Post by thyriel on 2011-10-31
Thanks that did it :)

---

