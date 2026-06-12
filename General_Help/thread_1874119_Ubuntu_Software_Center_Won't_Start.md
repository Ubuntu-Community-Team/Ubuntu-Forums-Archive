---
title: "Ubuntu Software Center Won't Start"
date: 2011-11-02
forum: General Help
---

### Post by RichardC400 on 2011-11-02
I am running Oneric Ocelot ..11.10 i think.
anyway once i click 'ubuntu software center' it does nothing.
when i run

```
sudo software-center
```

i get


```
2011-11-02 16:40:45,405 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 212, in __init__
    self.cache.open()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 209, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 93, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 140, in open
    self._list.read_main_list()
SystemError: E:Malformed line 64 in source list /etc/apt/sources.list (dist parse)
```

any way to fix this?

---

### Post by 2F4U on 2011-11-02
Seems as if there is a problem in your /etc/apt/sources.list that you should correct. I would look around line 64.

---

### Post by RichardC400 on 2011-11-02
Okay i checked line 64 which has:

> deb [http://gb.archive.ubuntu.com/ubuntu/natty](http://gb.archive.ubuntu.com/ubuntu/natty) universe

and below that there is the

> deb-src [http://gb.archive.ubuntu.com/ubuntu/natty](http://gb.archive.ubuntu.com/ubuntu/natty) universe

---

### Post by mörgæs on 2011-11-02
You need to remove all references in sources.list to versions other than 11.10.

---

### Post by RichardC400 on 2011-11-02
> **mörgæs said:**
> You need to remove all references in sources.list to versions other than 11.10.

Thanks, this worked.
I removed the natties out of it, saved it and ran

```
sudo software-center
```

and it opened.

Thank you very much guys

---

