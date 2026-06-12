---
title: "error after typing gksu nautilus"
date: 2011-10-29
forum: General Help
---

### Post by xavi fernandez on 2011-10-29
Hi all!!! I'm running ubuntu 11.04 is my first experience with Linux. When I type in terminal

gksu nautilus (I try use this command for change permissions from a folder I create already)

They give me this error:

@ubuntu:~$ gksu nautilus

(gksu:2270): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2270): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2270): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2270): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
** (nautilus:2272): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension

--- Hash table keys for warning below:
--> l1792
--> root
--> inode/directory

--- Hash table keys for warning below:
--> file:///
Shutting down nautilus-gdu extension

(nautilus:2272): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
@ubuntu:~$ 

Please, can you help me out with this??

Thanks in advance.

---

### Post by garvinrick4 on 2011-10-29
You are running a Live CD (install CD using Try Ubuntu.?

---

### Post by elliotn on 2011-10-29
alt f2 then type gksudo nautilus 
that works for me

---

### Post by Frogs Hair on 2011-10-29
See the link. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by robbielink on 2011-10-31
> **Frogs Hair said:**
> See the link. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Excellent reference!

---

### Post by drs305 on 2011-10-31
I get the 'hash' errors as well but nautilus runs fine.

There are numerous bug reports about the 'pixmaps' error messages. I was able to eliminate them by installing the following package:
```
sudo apt-get install gtk2-engines-pixbuf
```

---

