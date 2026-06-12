---
title: "Sonata Won't Start"
date: 2009-07-19
forum: General Help
---

### Post by dannymichel on 2009-07-19
I get this error:
```
2009-07-19 08:10:52  Connection lost while reading line
Traceback (most recent call last):
  File "/usr/bin/sonata", line 167, in <module>
    app = main.Base(args)
  File "/usr/lib/pymodules/python2.6/sonata/main.py", line 759, in __init__
    self.iterate_now()
  File "/usr/lib/pymodules/python2.6/sonata/main.py", line 1065, in iterate_now
    self.iterate()
  File "/usr/lib/pymodules/python2.6/sonata/main.py", line 1019, in iterate
    self.handle_change_status()
  File "/usr/lib/pymodules/python2.6/sonata/main.py", line 1547, in handle_change_status
    self.current.current_update(prevstatus_playlist, self.status['playlistlength'])
  File "/usr/lib/pymodules/python2.6/sonata/current.py", line 209, in current_update
    for track in changed_songs:
TypeError: 'NoneType' object is not iterable

```

---

### Post by dannymichel on 2009-07-20
anybody?

---

### Post by dannymichel on 2009-07-23
please?

---

### Post by dannymichel on 2009-07-26
interesting.

---

### Post by dannymichel on 2009-07-27
anybody out there?

---

### Post by whitethorn on 2009-07-27
do any other clients work?  Such as gmpc?  If you want you could go to the Sonata homepage and download the newer version of the client see if it works with that one.

---

### Post by dannymichel on 2009-07-27
Sure all other mpc clients work. I've tried the most recent version

---

### Post by dannymichel on 2010-04-29
a year later, same problem. any help would be greatly appreciated

---

### Post by dannymichel on 2010-04-30
haha, oh boy

---

