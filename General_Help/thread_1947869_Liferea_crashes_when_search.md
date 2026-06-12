---
title: "Liferea crashes when search"
date: 2012-03-27
forum: General Help
---

### Post by palimmo on 2012-03-27
Hi!
I'm using Liferea 1.8.0 (from liferea-team ppa) and I find it very good.
The only problem is when I perform a search: it crashes.
Fortunately, this happens only the first 2-3 times... then it works correctly and I can perform search without problems. Until the next reboot.


Here I post what the Terminal reports:
```
alessio@alessio-ubuntu:~$ liferea

(liferea:14237): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(liferea:14237): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(liferea:14237): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(liferea:14237): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(liferea:14237): GLib-CRITICAL **: g_strstr_len: assertion `haystack != NULL' failed

Liferea did receive signal 11 (Segmentation fault).
You have probably triggered a program bug. I will now try to 
create a backtrace which you can attach to any support requests.

```


Liferea 1.8.0
Ubuntu 11.10 64 bit

Thanks in advance for any help!

---

### Post by palimmo on 2012-03-29
Today I've updated to 1.8.3.
I'll see soon if there is the same problem.

---

### Post by markus.s on 2012-04-27
same problem here...

search-folders didn't find new entries
crashes only on click on search-folder container

Liferea did receive signal 11 (Speicherzugriffsfehler).
You have probably triggered a program bug. I will now try to 
create a backtrace which you can attach to any support requests.

removed ubuntu package
get 1.8.5 source from sourceforge --> same problem
get 1.6.8 source from sourceforge --> works

rgds, markus

---

