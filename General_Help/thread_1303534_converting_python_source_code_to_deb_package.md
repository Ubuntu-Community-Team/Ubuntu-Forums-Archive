---
title: "converting python source code to deb package"
date: 2009-10-28
forum: General Help
---

### Post by mlinuxuser on 2009-10-28
I want to conver the python code to debain package for my ubuntu 9.04.
the source code is in 
[http://code.google.com/p/vdown/](http://code.google.com/p/vdown/)

THat debain package is for older versions. To use it in my ubuntu 9.04, How to compile? and make it to deb package?

---

### Post by Giblet5 on 2009-10-28
Deleted link to building Debian packages cuz I'm dumb.

---

### Post by alphaniner on 2009-10-28
I looked at the files in the package and it looks like you don't need to compile anything.  Just follow the instructions in the file INSTALL:

```

$ cat INSTALL 
To install vdown and gvdown, do, as root:
# nonsrc/setup.sh
(sudo in Ubuntu & derivatives)
To remove it, just execute
# nonsrc/remove.sh

License: GNU General Public License v3
(c) 2007-2008 Nicolai Spohrer <nicolai@xeve.de>
$ 

```

---

### Post by mlinuxuser on 2009-10-28
Thank u very much

---

### Post by mlinuxuser on 2009-10-28
I post wrongly
Oh THe Icon shown in applicatons->internet->..        but now started.

---

### Post by mlinuxuser on 2009-10-29
> **mlinuxuser said:**
> Oh THe Icon shown in applicatons->internet->..        but now started.
THe Icon shown in applicatons->internet->..        but now it is not started.

---

