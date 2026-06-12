---
title: "Where does ubuntu store package information?"
date: 2010-10-26
forum: General Help
---

### Post by RageLtMan on 2010-10-26
Synaptic and update-xapian-index both keep locating the name of a package that is not installed on my system and causing errors as a result, i was wondering if anyone knew what files these scripts search to get a list of packages and how i could edit said files to remove references to the offending package? The messages i get from synaptic and update-xapian look like this:

File "/usr/sbin/update-apt-xapian-index", line 699, in <module>
res = updateIndex(dbpath, addons, progress)
File "/usr/sbin/update-apt-xapian-index", line 350, in updateIndex
for idx, pkg in enumerate(cache):
File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 161, in __iter__
yield self[pkgname]
File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 154, in __getitem__
pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: 'libghc6-edison


and

Rebuilding Xapian index... 94%
Traceback (most recent call last):
File "/usr/sbin/update-apt-xapian-index", line 720, in <module>
buildIndex(dbdir, addons, progress)
File "/usr/sbin/update-apt-xapian-index", line 389, in buildIndex
for idx, pkg in enumerate(cache):
File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 161, in __iter__
yield self[pkgname]
File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 154, in __getitem__
pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: 'libghc6-edison

the package, lighc6-edison is something i ended up putting together manually but it can be removed from the package list entireley although i've no idea how to do this. Thanks

---

### Post by dcstar on 2010-10-27
> **RageLtMan said:**
> 
..........
the package, lighc6-edison is something i ended up putting together manually but it can be removed from the package list entireley although i've no idea how to do this. Thanks

```
man apt-get | grep purge
```

---

### Post by Drenriza on 2010-10-27
From what i understand you want to remove lighc6-edison ?

---

### Post by RageLtMan on 2010-10-27
Its not installed, not as a debian package anyway, but there's a reference to it somewhere in the xapian index. apt-get purge cant get rid of a package thats not installed, the reference to it is wrong, partial, remnant, something odd... i need to find out which files actually have ALL the package information, grep through them, and yank the bad ref.

---

### Post by stoneage on 2010-10-27
You could try /var/cache/apt/archives

Also maybe sudo apt-get install -f

---

### Post by RageLtMan on 2010-10-27
the archives dir stored DEB files, and aptitude, dpkg, synaptic, etc do NOT think that this package is installed at all, they just get messed up on the reference to it.

---

### Post by RageLtMan on 2010-10-27
SOLUTION - removed everything from /var/lib/apt/lists, ran apt-get update to build new lists, ran update-xapian-index. Voila, done.

---

