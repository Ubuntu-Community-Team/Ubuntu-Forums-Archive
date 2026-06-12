---
title: "svn-load says &quot;unhandled exception in callback_get_login&quot;"
date: 2009-12-11
forum: General Help
---

### Post by 00000 on 2009-12-11
I'm using svn-load (package name is `svn-load') in Karmic, 64-bit, which is a replacement for the svn-load-dirs script in subersion.  I get the following error (after a lot of `Adding ' statements):

...
Adding /tmp/svn-load_XPB6K/working/libltdl/loaders/dlopen.c
Adding /tmp/svn-load_XPB6K/working/libltdl/loaders/load_add_on.c
Adding /tmp/svn-load_XPB6K/working/libltdl/slist.c
Warning: Unimplemented callback: get_login
TypeError: PyCXX: Error creating object of type N2Py5TupleE from None
Traceback (most recent call last):
  File "/usr/bin/svn-load", line 650, in <module>
    "Load %s into %s." % (os.path.basename(d), import_dir))
pysvn._pysvn_2_6.ClientError: unhandled exception in callback_get_login

Does anyone use this script (and have this problem with it)?

---

