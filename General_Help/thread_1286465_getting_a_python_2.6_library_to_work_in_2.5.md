---
title: "getting a python 2.6 library to work in 2.5"
date: 2009-10-09
forum: General Help
---

### Post by pfs1 on 2009-10-09
I'm currently doing a project in blender, and I'm using the cwiid library for communicating with a wiimote.

Blender uses python 2.5, so I installed that 2.5 alongside 2.6.  However, it seems I cann't import cwiid when working in blender (or in the 2.5 shell).  However, it DOES import when working in the 2.6 shell.

A find|grep confirms that cwiid has an .so and docfiles for 2.6, but nothing for 2.5.

I'm relatively new to this kind of thing.  What would be the best way to get cwiid working on 2.5?  Is there a way to symlink the library into 2.5?  Are 2.5 and 2.6 similar enough that won't cause any problems?  Or do I need to compile cwiid from source specifically for 2.5?  Cwiid used to be compiled for 2.5 so I can't imagine too much has changed.

If anyone familiar with working with libraries can point me in the right direction, I'd really appreciate it.  And apologize if this isn't the right section- I wasn't sure where else the topic would fit.

---

### Post by hardyn on 2009-10-09
I have only once had a problem sym linking a newer lib. to an older path... try it.

---

### Post by pfs1 on 2009-10-09
OKay, just gave it a shot.  This is all the cwiid related files in /usr:

```
./share/python-support/python-cwiid
./share/python-support/python-cwiid/cwiid-0.6.00-py2.6.egg-info
./share/doc/python-cwiid                                       
./share/doc/python-cwiid/changelog.Debian.gz                   
./share/doc/python-cwiid/AUTHORS                               
./share/doc/python-cwiid/copyright                             
./share/doc/python-cwiid/changelog.gz
./share/doc/python-cwiid/NEWS.gz
./share/doc/python-cwiid/README.gz
./share/doc/libcwiid1
./share/doc/libcwiid1/changelog.Debian.gz
./share/doc/libcwiid1/AUTHORS
./share/doc/libcwiid1/copyright
./share/doc/libcwiid1/changelog.gz
./share/doc/libcwiid1/NEWS.gz
./share/doc/libcwiid1/README.gz
./lib/cwiid
./lib/cwiid/plugins
./lib/cwiid/plugins/acc.so
./lib/cwiid/plugins/ir_ptr.so
./lib/cwiid/plugins/nunchuk_acc.so
./lib/python-support/python-cwiid
./lib/python-support/python-cwiid/python2.6
./lib/python-support/python-cwiid/python2.6/cwiid.so
./lib/libcwiid.so.1
./lib/libcwiid.so.1.0
```

Given those files, I symlinked "python2.5" to python2.6 in the python-cwiid directory and thought that would do the trick.  However, in py2.5, it still says the module doesn't exist when I try to import it.

If symlinking was going to fail, I'd have expected a mess when running the script or a message from the interpreter that the library is incompatible.  The fact it's still not seeing it at all makes me wonder if I've symlinked it properly in the first place.  Can anyone confirm if I'm doing it right?

---

