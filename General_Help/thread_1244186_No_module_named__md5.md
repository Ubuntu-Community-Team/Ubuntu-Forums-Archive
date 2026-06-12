---
title: "No module named _md5"
date: 2009-08-19
forum: General Help
---

### Post by carloc on 2009-08-19
Hi Everyone,

I always get this error when starting reviewboard, the error went away already but somehow after updates, the error came back.. It seems to be an error with the python distribution

Anyone of you familiar with this error?
> 
ImportError: No module named _md5
[Wed Aug 19 17:47:26 2009] [error] get_interpreter: no interpreter callback found.
[Wed Aug 19 17:47:26 2009] [error] [client 192.168.1.27] python_handler: Can't get/create interpreter.
[Wed Aug 19 17:47:26 2009] [error] [client 192.168.1.27] File does not exist: /var/www/errordocs
[Wed Aug 19 17:56:27 2009] [error] make_obcallback: could not call init.\n
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/mod_python/apache.py", line 937, in init
    from mod_python import importer
  File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 24, in <module>
    from mod_python import publisher
  File "/usr/lib/python2.5/site-packages/mod_python/publisher.py", line 50, in <module>
    from cache import ModuleCache, NOT_INITIALIZED
  File "/usr/lib/python2.5/site-packages/mod_python/cache.py", line 27, in <module>
    import urllib2
  File "/usr/lib/python2.5/urllib2.py", line 91, in <module>
    import hashlib
  File "/usr/lib/python2.5/hashlib.py", line 133, in <module>
    md5 = __get_builtin_constructor('md5')
  File "/usr/lib/python2.5/hashlib.py", line 60, in __get_builtin_constructor
    import _md5
ImportError: No module named _md5
[Wed Aug 19 17:56:27 2009] [error] get_interpreter: no interpr


---

### Post by hwttdz on 2011-08-31
I'm replying to this old message because I've seen this message before and searched unsuccessfully for a resolution.  Searching the forums yielded fewer hits than I expected.  From looking at the files it mentions I think that this fix should still work.

"Jobs on Ubuntu 9.04 may fail with an error containing the message: ImportError: No module named _md5. This is most often caused by an inability to find the library libcrypto.so.6 that is provided by the operating system, because the library name is nonstandard.

To fix this problem, first ensure that the OpenSSL package is installed on your system (including the 32-bit packge if your OS is 64-bit), and then make the following symbolic link:

ln -s /lib/libcrypto.so.0.9.8 /lib/libcrypto.so.6

If your OS is 64-bit, then also make the following link:

ln -s /lib64/libcrypto.so.0.9.8 /lib64/libcrypto.so.6"

---

