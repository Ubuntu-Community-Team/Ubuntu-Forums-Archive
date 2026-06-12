---
title: "finding build dependencies of a package"
date: 2009-09-19
forum: General Help
---

### Post by sandyd on 2009-09-19
know i can install all the build dependencies of a package using sudo apt-get build-dep, but is theeere a way of listing all the build dependencies of a package without installing any of them?

---

### Post by Bachstelze on 2009-09-19
Use the -s (simulate) flag:

```
sudo apt-get -s build-dep foo
```

---

### Post by sandyd on 2009-09-19
how do i make it even packages that ive already installed?

---

### Post by drs305 on 2009-09-19
> **carlee said:**
> how do i make it even packages that ive already installed?

For a specific package, you can run:
```

apt-cache show *packagename*

```

To trim it a bit, you can run it like this (displays 6 lines after the Depends line:
```
apt-cache show packagename | grep -A6 Depends:
```

Or you can check the Properties > Dependencies of any package highlighted in Synaptic.

---

### Post by sandyd on 2009-09-19
> **drs305 said:**
> For a specific package, you can run:
```

apt-cache show *packagename*

```To trim it a bit, you can run it like this (displays 6 lines after the Depends line:
```
apt-cache show packagename | grep -A6 Depends:
```Or you can check the Properties > Dependencies of any package highlighted in Synaptic.
oops. sorry. i meant Build dependencies.

---

### Post by drs305 on 2009-09-19
> **carlee said:**
> oops. sorry. i meant Build dependencies.

Entirely my error. I guess the clue should have been that you stated *build dependencies* everywhere - even in the title.  ](*,)

Don't know the answer but I'll look around.

---

