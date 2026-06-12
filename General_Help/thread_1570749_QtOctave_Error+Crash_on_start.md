---
title: "QtOctave: Error+Crash on start"
date: 2010-09-08
forum: General Help
---

### Post by REDace0 on 2010-09-08
I'm running a relatively fresh installation of Ubuntu x64 in Virtualbox.Today I installed QtOctave using
```
sudo apt-get install qtoctave
```
apt-get did its thing, found all the dependencies (there are many, since octave depends on the major linear algebra libraries). When all was said and done, it seemed to install correctly. Octave works, for example. However, when I try to run QtOctave, I get the following error message at start:
```
/tmp/qtoctave-bin/bin/qtoctave can not be opened
```
Now, I know why it can't be opened. That file (and parent directory, and that directory's parent directory) does not exist. The rest of the front-end appears to run and load perfectly, but when I close the error window, the program exits. Has anyone else encountered this problem? Found a solution? I'm thinking this may be a 64-bit issue, but don't really know.

Thanks.

---

### Post by REDace0 on 2010-09-21
Update: It now works if I```
sudo qtoctave
```

---

