---
title: "libtiff.so.3 wrong ELF class: ELFCLASS32"
date: 2011-06-08
forum: General Help
---

### Post by pizzaia on 2011-06-08
Hi, I'm having this error when trying to launch maya 2011 on my ubuntu. I don't understand what it means. 

/usr/autodesk/maya2011-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: wrong ELF class: ELFCLASS32

How can I solve this??

root@Scarface-Linux:/usr/lib# ldconfig -v |grep libtiff
/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
    libtiff.so.4 -> libtiff.so.4.3.3
/sbin/ldconfig.real: File /usr/local/lib/libtiff.so.3 is empty, not checked.
    libtiff.so.4 -> libtiff.so.4.3.3
/sbin/ldconfig.real: File /usr/lib/libtiff.so.4 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libtiff.so.3 is empty, not checked.

Thanks for the help.

---

### Post by pizzaia on 2011-06-08
Any suggestions?? Please!

---

### Post by pizzaia on 2011-06-08
I think that there's a problem with the libtiff.so.3 file, but I search about this error around the internet and I could not find anything.  I will appreciate if someone could help me with this.

---

