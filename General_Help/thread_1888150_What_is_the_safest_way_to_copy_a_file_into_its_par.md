---
title: "What is the safest way to copy a file into its parent's parent directory?"
date: 2011-11-28
forum: General Help
---

### Post by saphil on 2011-11-28
I think this should copy all *.waa files from 2 directories down to the directory above, and without attempting to copy the files to all grandparent sibling directories.
```
$ cp -R ./*/*/*/*.waa ./*/*/

```Is this a really bad idea?  My experiments with test systems seem to bear out my assumption.

---

### Post by searchfgold6789 on 2011-11-28
Not sure exactly what your goal is, but try leaving out the -R.
edit: I just realized that this is my 100th bean. cool.

---

### Post by linuxrev on 2011-11-28
Well, I'd do it the lazy way, either using Midnight Commander ('mc') on console level, or Krusader in a graphic environment.

---

### Post by Vaphell on 2011-11-28
try something like this
```
for f in ./*/*/*/*.waa; do cp -v "$f" "${f%/*/*}"; done
```

---

### Post by saphil on 2011-11-28
> **Vaphell said:**
> try something like this
```
for f in ./*/*/*/*.waa; do cp -v "$f" "${f%/*/*}"; done
```

Thanks! this is what I was looking for.

---

### Post by saphil on 2011-11-28
> **searchfgold6789 said:**
> Not sure exactly what your goal is, but try leaving out the -R.
edit: I just realized that this is my 100th bean. cool.

You have reached your thousandth bean. Congratulations!  
I am trying to move a bunch of files so I can zip them together in a higher folder.

The data is very hard to automate against, as the file structure is arbitrarily deep, very large,  and not all the information arrives at once.  I am lashing together a series of scripts to handle the mess and am hopefull that I can understand what I was trying to accomplish in a month when the event hits again.

---

