---
title: "Python2.5"
date: 2009-09-09
forum: General Help
---

### Post by zelhar on 2009-09-09
If I install python 2.5 (or any previous version for that matter), would it replace python2.6 as the default python on my system ?

I don't want it to. I only want it to work when I specifically use python2.5 or whatever its specific command line is.

---

### Post by eric3_14159 on 2009-10-08
I don't believe so. If it does, just run
```
sudo rm /usr/bin/python
sudo ln -s /usr/bin/python2.6 /usr/bin/python
```
And then the default will be Python 2.6 again.

---

