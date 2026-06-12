---
title: "Problem of installers in my ubuntu fork (without gnome)."
date: 2010-11-26
forum: General Help
---

### Post by moscwich on 2010-11-26
I was make the fork out ubuntu alternate (installed without grphical) and compile by squashfs-tools.
I was added package ubiquity and ubiquity-frontend-gtk.
At the install, after applying the partitioning - "Fatal error" and aborting install.

live-installer-launcher - aborting immediately:
```
$ sudo live-installer-launcher
no suitable d-i initrd image found, aborting.
```

/var/log/syslog (before aborting, 10 sec., after 7 sec.):

```
Oct 18 21:02:10 ubuntu ubiquity: /usr/lib/python2.6/dist-packages/apt/deprecation.py:96: UserWarning: Deprecated parameter 'autoFix'
Oct 18 21:02:10 ubuntu ubiquity:   warnings.warn("Deprecated parameter %r" % key)
Oct 18 21:02:10 ubuntu python: Exception during installation:
Oct 18 21:02:10 ubuntu python: Traceback (most recent call last):
Oct 18 21:02:10 ubuntu python:   File "/usr/share/ubiquity/install.py", line 608, in <module>
Oct 18 21:02:10 ubuntu python:     install.run()
Oct 18 21:02:10 ubuntu python:   File "/usr/share/ubiquity/install.py", line 122, in run
Oct 18 21:02:10 ubuntu python:     self.copy_all()
Oct 18 21:02:10 ubuntu python:   File "/usr/share/ubiquity/install.py", line 299, in copy_all
Oct 18 21:02:10 ubuntu python:     assert os.path.exists(fs_size), "Missing filesystem.size."
Oct 18 21:02:10 ubuntu python: AssertionError: Missing filesystem.size.
Oct 18 21:02:10 ubuntu python:
```
(this is old problem for me)

I think, problem with define the size of the file system, but I'm not sure.

Please, help me!

[B][LIST]
[*][partman-log](http://al-moscwich.narod.ru/data/partman.txt)
[*][syslog](http://al-moscwich.narod.ru/data/syslog.txt)
[/LIST][/B]

[SIZE="1"]p.s.
*Maybe I'm not to correctly speak (interprets), becouse I don't not know English, I apologize in advance.*[/SIZE]

---

