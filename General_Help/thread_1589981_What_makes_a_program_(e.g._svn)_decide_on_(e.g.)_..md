---
title: "What makes a program (e.g. svn) decide on (e.g.) .so.0 instead of .so?"
date: 2010-10-07
forum: General Help
---

### Post by rob_l_f on 2010-10-07
I'm having a nightmare of a time trying to build a system in our department, but now the weirdest thing has happened:  Amongst all the problems with building that software, subversion now says:

svn: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

This is an error I was having with some of my own systems, but what on earth caused this?  I haven't touched libexpat, and apt-get still thinks it is installed - which it is, as libexpat.so, not libexpat.so.0.  Can anyone shed any light on what might have caused this, and what makes a program such as svn choose some particular library?  Any suggestions are welcome since I don't really know what is at fault yet!

Many thanks.

---

### Post by luigi_mb on 2010-10-07
Try to set up a symlink

```

ln -s libexpat.so ibexpat.so.0

```

/luigi

---

