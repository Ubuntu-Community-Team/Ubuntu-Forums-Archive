---
title: "How to install Kdevelop4 while keeping Kdevelop3"
date: 2009-10-02
forum: General Help
---

### Post by wolfie2x on 2009-10-02
I like to try kdevelop4 beta5 on my Ubuntu 9.04, but need to keep my kdevelop3 intact. Appreciate any help. (Couldn't find anything on google).

---

### Post by sedawk on 2009-10-02
What you can try to do is to get the sources of the new
version and install everything to a new directory, e.g.
/home/<user>/kd4

With many open source products it works like this:

```

#unpack sources and go to unpacked directory
./configure --prefix=/home/<user>/kd4
make
make install

```

I'm not sure this is the standard procedure for KDE stuff,
it might be slightly different (qmake instead of make?)

E.g I have a directory /home/<user>/extra810 (for Ubuntu 8.10)
that contains all the software I compiled myself and that
is not included in Ubuntu. It contains software that
is missing from Ubuntu or newer versions or ...

---

### Post by wolfie2x on 2009-10-03
I was a bit impatient so I uninstalled kdevelop3 and installed kdevelop4. So far it looks ok.. (I had to update qt by adding ppa).
The kdevelop4 version I got was 3.9.91. beta5 is 3.9.95. Hope sedawk's steps will work..

---

