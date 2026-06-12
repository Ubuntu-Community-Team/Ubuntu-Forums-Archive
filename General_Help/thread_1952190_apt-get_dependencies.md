---
title: "apt-get dependencies"
date: 2012-04-03
forum: General Help
---

### Post by tkeith on 2012-04-03
I apt-get installed libapache2-mod-wsgi, which automatically installed libpython2.6, python2.6, and python2.6-minimal. I then apt-get removed libapache2-mod-wsgi, and then ran apt-get autoremove. This removed libpython2.6, but not python2.6 or python2.6-minimal. Why aren't these other dependencies autoremoved?

---

### Post by raja.genupula on 2012-04-04
Actually python is pre-installed in Ubuntu .

many of things in ubuntu need python .

---

### Post by tkeith on 2012-04-04
> **raja.genupula said:**
> Actually python is pre-installed in Ubuntu .

many of things in ubuntu need python .

Python 2.7 is pre-installed, but 2.6 is not. It only was installed as a dependency. My question remains.

---

### Post by raja.genupula on 2012-04-04
try to remove them , you can make it from the synaptic and software center , look the version and then remove it .

---

### Post by tkeith on 2012-04-04
> **raja.genupula said:**
> try to remove them , you can make it from the synaptic and software center , look the version and then remove it .

I understand how to remove it, but I want to understand why it isn't automatically removed with "apt-get autoremove".

---

### Post by cortman on 2012-04-04
From the man page-

>   autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.


Apparently some other package depends or thinks it depends on the python 2.6 packages, or else

```
sudo apt-get purge
```

might have been a better option.

---

### Post by tkeith on 2012-04-05
> **cortman said:**
> From the man page-



Apparently some other package depends or thinks it depends on the python 2.6 packages, or else

```
sudo apt-get purge
```might have been a better option.

Is there a way to see what package still depends on python2.6 and python2.6-minimal?

---

### Post by cortman on 2012-04-05
> **tkeith said:**
> Is there a way to see what package still depends on python2.6 and python2.6-minimal?

Yes, with debfoster, available in the repositories.

---

