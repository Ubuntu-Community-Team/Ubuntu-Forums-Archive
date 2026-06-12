---
title: "Xemacs won't launch -- fedora font problem now afflicting ubuntu?"
date: 2010-01-11
forum: General Help
---

### Post by LeFou on 2010-01-11
I just did a 
sudo apt-get install xemacs21

then
xemacs21

and got
Warning: Missing charsets in String to FontSet conversion
Fatal error: assertion failed, file insdel.c, line 2376, (nonreloc && NILP (reloc)) || (!nonreloc && STRINGP (reloc))

which looks like
[https://bugzilla.redhat.com/show_bug.cgi?id=478370](https://bugzilla.redhat.com/show_bug.cgi?id=478370)

... a bug that is fixed by installing "xorg-x11-fonts-misc"

... which gives me
E: Couldn't find package xorg-x11-fonts-misc

---

