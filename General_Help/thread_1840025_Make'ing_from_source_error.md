---
title: "Make'ing from source error"
date: 2011-09-06
forum: General Help
---

### Post by shang1 on 2011-09-06
I am trying to compile infomap from source: [http://infomap-nlp.sourceforge.net/](http://infomap-nlp.sourceforge.net/)

However I get an error:

checking gdbm/ndbm.h usability... no
checking gdbm/ndbm.h presence... no
checking for gdbm/ndbm.h... no

Despite having the libraries installed:

i   libgdbm-dev 
i   libgdbm3  

Does anyone know what I am missing here?
Using Kubuntu.

---

### Post by Beacon11 on 2011-09-07
Those aren't actually errors, it's just trying to find that file. If it didn't find it, it would fail and give you a real error. Can you paste in more of the log?

---

### Post by gmargo on 2011-09-07
It looks to me like the **configure.ac** file needs some work to account for the renaming of "gdbm/ndbm.h" to "gdbm-ndbm.h" from the **libgdbm-dev** package.

But instead of that, a simple symbolic link hack seems to make it all work, so try this:
```

cd /usr/local/include
sudo ln -s /usr/include/gdbm-ndbm.h ndbm.h

```

---

