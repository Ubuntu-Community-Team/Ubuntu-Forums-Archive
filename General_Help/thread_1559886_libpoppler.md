---
title: "libpoppler"
date: 2010-08-24
forum: General Help
---

### Post by jaapkroe on 2010-08-24
There is still a problem with evince (or poppler) in ubuntu.
For some pdf-documents Poppler generates the eror
Error: Illegal entry in bfrange block in ToUnicode CMap

For examples, see
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=578051](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=578051)
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/620751](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/620751)
[https://bugzilla.redhat.com/show_bug.cgi?id=574964](https://bugzilla.redhat.com/show_bug.cgi?id=574964)

This bug was solved on april 2010:
[https://bugs.freedesktop.org/show_bug.cgi?id=27728](https://bugs.freedesktop.org/show_bug.cgi?id=27728)

I've installed the new poppler lib to */usr/lib* as such
```
cd 
wget http://poppler.freedesktop.org/poppler-0.14.2.tar.gz
tar -xf poppler-0.14.2.tar.gz
cd poppler-0.14.2/
./configure 
sudo make install
```

But it doesn't work, perhaps evince is compiled statically or I did something wrong.
It would be nice if someone can implement this change in ubuntu because it is a really annoying bug.

For now, here's a quick fix. 
Add the following line to your ~/.bashrc
```
function evince() { /usr/bin/evince "$@" 2>/dev/null; }

```

Cheers

---

