---
title: "Beagle eating my memory"
date: 2005-02-12
forum: General Help
---

### Post by valfader on 2005-02-12
I have a wired "bug" in beagle, after I start beagled (0.0.5) it starts to eat all my memory, and after some time (30 min) all my memory (756MB+1,2 GB) is allocatet and the app is killed by the kernel. And it does not seem to care that I have put the .noindex files in most dirs.
Any one else with the same problem? Any solutions?

---

### Post by freeflight on 2005-02-23
I have the same issue with Beagle on my Hoary.

I made several tests without beeing able to make it work :
1. Beagle 0.0.3 + Warthy
2. Beagle 0.0.5 + Warthy
3. Beagle 0.0.5 + Hoary

Each time i launch # beagle --fg --debug, it begin to consume all my memory while indexing and then swap...

I try with a smaller test case (a new homedir with a few files) and the result is the same  :? 

Maybe some of us should post a bug entry in beagle bugzilla...?

---

### Post by GilGalad on 2005-02-23
I had same problem but it was resolved with beagle 0.0.6.1.

---

### Post by yatesco on 2005-02-23
How did you get it installed?  I tried to follow the Houry/Beagle wiki, but I cannot install mono, apt states it is not there.  I have added links to universe/multiverse and I can see monodoc, mono-mcs etc., but no mono :(

Any ideas?

Col

---

### Post by GilGalad on 2005-02-23
mono is in Hoary universe:

[http://archive.ubuntu.com/ubuntu/pool/universe/m/mono/](http://archive.ubuntu.com/ubuntu/pool/universe/m/mono/)

I think I just followed the wiki. You need to install the development version of the all the .NET bindings for gconf, glib, etc...

---

### Post by yatesco on 2005-02-23
But not for amd64 it would seem :(

---

### Post by GilGalad on 2005-02-23
Right. But are you sure you need the mono package. I mean there is nothing in that package but directories:

```

$ wajig listfiles mono
/.
/usr
/usr/share
/usr/share/doc
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/mono
/usr/share/doc/mono

```

---

