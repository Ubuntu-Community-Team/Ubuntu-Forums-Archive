---
title: "amd64 nautilus-gksu not in context menu"
date: 2011-10-14
forum: General Help
---

### Post by ds_shellback on 2011-10-14
Installed nautilus-gksu from terminal on amd64 bit system - "Open As Administrator" doesn't show up in the context menu as I'd expect.

Is this a known bug related to this debian bug report?

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=520511]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=520511")

How do I fix this - the whole point of this is to add the entry in the context menu!

---

### Post by ds_shellback on 2011-10-15
Ok, found this bug report which gives a temporary fix 

[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/817383]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/817383")

```
sudo cp /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0/
```

It seems this bug has been about for a while!

---

### Post by ds_shellback on 2011-10-15
ok, still need help:

The entry "Open as Administrator" is now in the context menu after copying the file as last post, but although it fires up a window asking for admin password - absolutely nothing else happens after that!

I think this problem is specifically related to amd64 bit installs, since I just done another 32bit install without any problem.

---

