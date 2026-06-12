---
title: "problems with flickrfs"
date: 2010-08-02
forum: General Help
---

### Post by hwttdz on 2010-08-02
I've tried to install flickrfs, however I'm having some troubles.  

Output of flickrfs ~/flickr_photos

```
/usr/share/pyshared/flickrfs/flickrapi.py:63: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Authorizing with flickr...
Authorization complete.
Sets are being populated in the background. Please wait...
Sets have been populated. Done.
Exception RuntimeError: 'maximum recursion depth exceeded while calling a Python object' in <type 'exceptions.AttributeError'> ignored
Exception RuntimeError: 'maximum recursion depth exceeded while calling a Python object' in <type 'exceptions.AttributeError'> ignored
Exception RuntimeError: 'maximum recursion depth exceeded while calling a Python object' in <type 'exceptions.AttributeError'> ignored
```

Then:

ls flickr_photos 
ls: cannot access flickr_photos: Invalid argument

and 
ls -l
ls: cannot access flickr_photos: Invalid argument
total 1492
drwxr-xr-x  3 user user   4096 2010-01-21 15:52 Archives/
drwxr-xr-x  3 user user   4096 2010-07-27 11:10 bin/
drwxr-xr-x  8 user user   4096 2010-08-02 12:42 Desktop/
drwxr-xr-x  5 user user   4096 2010-07-14 18:46 Documents/
drwxr-xr-x  4 user user   4096 2010-07-27 10:35 Downloads/
d?????????  ? ?       ?            ?                ? flickr_photos/

Is troubles.  Also dfo (desktop flickr uploader) does not work.  jUploader (which is not in the repo to my knowledge, but is available from sourceforge (linked to by flickr)) does.

---

### Post by ubunaut on 2010-09-04
This is a known bug in flickrfs [https://bugs.launchpad.net/ubuntu/+source/flickrfs/+bug/399452](https://bugs.launchpad.net/ubuntu/+source/flickrfs/+bug/399452)

There are some workarounds, but they may or may not work.

---

