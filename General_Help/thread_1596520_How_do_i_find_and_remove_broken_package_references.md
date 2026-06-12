---
title: "How do i find and remove broken package references?"
date: 2010-10-14
forum: General Help
---

### Post by RageLtMan on 2010-10-14
A while back a disk error caused /var/lib/dpkg/status to go south - completely corrupted. I managed to rebuild it with the help of a script i found online, but now there's a package called libghc6-edison in limbo on my install. It has no sources, as it was custom built, and i cant seem to find the references to this thing. Apt cache shows that it exists, synaptic gives me an error in CLI every time i launch it referring to this package -Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 699, in <module>
    res = updateIndex(dbpath, addons, progress)
  File "/usr/sbin/update-apt-xapian-index", line 350, in updateIndex
    for idx, pkg in enumerate(cache):
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 161, in __iter__
    yield self[pkgname]
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 154, in __getitem__
    pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: 'libghc6-edison

 I've tried grepping all the files in /var/lib/dpkg to no avail. Any ideas where else this information could be stored? i need to find all the references to the package and purge them. It seems to preven me from successfully pulling off a do-release-upgrade (in a VM for testing) as well as doing a remastersys dist (have to do remastersys backup  instead). 

The package was never available in Lucid, if i remember correctly, i had to compile it myself and debianize it, but i cant seem to find the sources on my build VM or anywhere in the installed end-product OS.

---

### Post by Quackers on 2010-10-14
In Synaptic Package Manager at the bottom left of the screen are any broken packages shown? Just an idea.

---

### Post by lordberic on 2010-10-14
Have you tried running 

sudo apt-get -f install

If you are getting errors in synaptic and with apt-get this might solve it

maybe try 

sudo apt-get purge libghc6-edison

---

### Post by RageLtMan on 2010-10-14
No broken packages, and attempting a purge results in apt-get saying it could not find the package. Package isnt there... not showing as installed or anything, just has some stale reference to it in the ether :(

---

### Post by RageLtMan on 2010-10-16
anyone else have any ideas?

---

### Post by drs305 on 2010-10-16
> **RageLtMan said:**
> anyone else have any ideas?

What happens if you run:
```
sudo update-apt-xapian-index
```

---

### Post by RageLtMan on 2010-10-18
attempting to rebuild the index results in the same:

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

---

