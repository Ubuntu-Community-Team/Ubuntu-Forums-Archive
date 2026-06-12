---
title: "Python errors cropping up"
date: 2010-02-24
forum: General Help
---

### Post by sublimation on 2010-02-24
I've been playing around upgrading a few things, and I've begun to see errors in strange places. Deluge (installed from source 1.2.1) complains about starting the core and gives an error log ending in 
```
File "/usr/local/lib/python2.6/dist-packages/deluge-1.2.1-py2.6.egg/deluge/core/core.py", line 82, in __init__
    sys.exit(1)
NameError: global name 'sys' is not defined
```
After getting sick of trying to track down the reason, I decided to move on and rip a new CD of mine. Using MusicBrainz to tag I discovered that it was unable to save the files properly, and checking that log gave me the following: 
```
E: 139783838770928 12:50:25 Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/picard/util/thread.py", line 80, in generic_run_item
    result = func()
  File "/usr/lib/pymodules/python2.6/picard/file.py", line 144, in _save_and_rename
    self._save(old_filename, metadata, settings)
  File "/usr/lib/pymodules/python2.6/picard/formats/id3.py", line 274, in _save
    tags.save(encode_filename(filename), v2=3, v1=v1)
  File "/usr/lib/pymodules/python2.6/picard/formats/mutagenext/compatid3.py", line 124, in save
    f.seek(-128, 2)
IOError: [Errno 95] Operation not supported
```


leading me to believe that perhaps my problems are stemming from a common source, the fact that I rebuilt python this morning through apt-build.

any suggestions for tracking down my troubles?

---

