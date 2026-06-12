---
title: "apt download dependencies"
date: 2009-10-05
forum: General Help
---

### Post by desperateone on 2009-10-05
I'd like to download a package and all of its dependencies. When I run  apt-get build-dep -d ghc6, I get some random packages, but not the main package (it's already installed here and this somehow makes sense to apt-get even though its .deb isn't in the archives folder). Then I got the main package from other sources, and it tells me that it has 8 dependencies, and not a single one of these is in the packages I downloaded in the first place. What is going on. Isn't there a simple way to download a package and all its dependencies?

Also, this. 

> sudo apt-get install -d ghc6
[..]
Note, selecting ghc6 instead of ghc
ghc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 124 not upgraded.

How does that make any sense? I just want to download the damn package.

---

### Post by credobyte on 2009-10-05
You've already downloaded it:
```
0 upgraded, 0 newly installed, 0 to remove and **[COLOR=Green]124 not upgraded[/COLOR]**.
```

---

### Post by desperateone on 2009-10-05
> **credobyte said:**
> You've already downloaded it:
```
0 upgraded, 0 newly installed, 0 to remove and **[COLOR=Green]124 not upgraded[/COLOR]**.
```

I don't think so. I got nothing for [FONT="Courier New"]sudo locate "*.deb" | grep ghc[/FONT]

---

### Post by credobyte on 2009-10-05
```
sudo aptitude show ghc6 | grep State
```

What's the output ?

---

### Post by desperateone on 2009-10-05
Installed, as expected.

---

### Post by desperateone on 2009-10-05
Okay, I managed to download the installed package with the graphical frontend. How about dependencies, how do I just download them automatically?

EDIT: Done that.

---

