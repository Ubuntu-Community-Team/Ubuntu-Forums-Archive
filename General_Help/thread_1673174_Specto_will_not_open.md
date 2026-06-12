---
title: "Specto will not open"
date: 2011-01-22
forum: General Help
---

### Post by 405jayb on 2011-01-22
I cant seem to get specto to work. When I run it from the terminal this is what I get.

jayb@jayb-laptop:~$ specto
/usr/lib/python2.6/dist-packages/spectlib/notifier.py:294: DeprecationWarning: PyArray_FromDimsAndDataAndDescr: use PyArray_NewFromDescr.
  for row in icon.get_pixels_array():
Traceback (most recent call last):
  File "/usr/bin/specto", line 30, in <module>
    specto = Specto()
  File "/usr/lib/python2.6/dist-packages/spectlib/main.py", line 128, in __init__
    self.watch_db.create(values)
  File "/usr/lib/python2.6/dist-packages/spectlib/watch.py", line 292, in create
    type = values[i]['type']
KeyError: 'type'

What does this mean?

---

### Post by 405jayb on 2011-03-08
my watches.list was corrupt

---

