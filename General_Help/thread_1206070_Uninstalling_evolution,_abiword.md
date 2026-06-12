---
title: "Uninstalling evolution, abiword?"
date: 2009-07-06
forum: General Help
---

### Post by TSWMIN85 on 2009-07-06
I'm trying to uninstall evolution and abiword, but everytime I do it uninstalls GNOME and GNOME DESKTOP ENVIRONMENT rendering me hopeless in a word full of Windows to find a solution.

Anyone?

By the way, I found how to reinstall GNOME but I just wanna get those two programs off. I have no use of them.

Thank you in advance.

---

### Post by Celauran on 2009-07-06
Evolution is an integral part of GNOME and cannot be removed. Some components can, but not the whole package.

---

### Post by Wiebelhaus on 2009-07-06
It's a meta-package , dependencies are broken and ubuntu-desktop gets removed. In other words they way Ubuntu was built this is impossible unless you build from the bottom up.

---

### Post by oldos2er on 2009-07-06
```
sudo aptitude remove evolution
```
worked for me. Can't speak to abiword since I've never installed it.

---

### Post by philcamlin on 2009-07-06
sudo apt-get remove abiword

you cant get rid of evolution its buit  into the system :popcorn:

---

### Post by credobyte on 2009-07-06
Evolution can be removed only partially ( don't --purge it !! ), so .. better leave it ;)

---

### Post by TSWMIN85 on 2009-07-07
> **oldos2er said:**
> ```
sudo aptitude remove evolution
```worked for me. Can't speak to abiword since I've never installed it.

What's the difference between doing

```
sudo apt-get remove evolution
```

and

```
sudo aptitude remove evolution
```

---

### Post by oldos2er on 2009-07-07
When I first started using Ubuntu, it was said that aptitude handled removing unneeded dependencies better than apt-get. I got into the habit of using aptitude, and still do so. I'm not sure of how the status of aptitude vs. apt-get is now; it may be there is no longer any difference between them.

 Despite the claims in this thread to the contrary, I have actually run **sudo aptitude remove evolution**, so I know it will work (at least on 9.04) without breaking Gnome or anything else. As always, backup any sensitive data before running any system-altering commands.

---

