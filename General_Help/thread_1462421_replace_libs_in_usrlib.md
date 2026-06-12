---
title: "replace libs in /usr/lib"
date: 2010-04-25
forum: General Help
---

### Post by mayapower on 2010-04-25
I have successfully compiled latest pixman/cairo from sources on "hardy". All the libs are in /usr/local/lib. How do I replace these with the ones installed in /usr/lib.

Or may be uninstall the old ones and install the newly built libraries.

Prashant

---

### Post by SnickerSnack on 2010-04-25
Well

```
cp /usr/lib/* /usr/local/lib
```

should do it.  It will over write the old ones.  If you wish to remove all of the files in /usr/local/lib (if they're *all* out-of-date), you can do

```
rm /usr/local/lib/*
```

first.

---

### Post by mayapower on 2010-04-25
Don't you think it's going to break the package. For example by default pixman 0.10 is installed along with debug version, docs, dev etc. If I'll replace only the libraries(actually I did), synaptic still shows pixman 0.10, where as I replace the new libraries of pixman 0.18.

Is there any standard replacement method or you just copy them?

Prashant

---

