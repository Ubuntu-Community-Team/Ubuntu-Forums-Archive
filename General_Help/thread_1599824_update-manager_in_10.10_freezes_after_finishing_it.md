---
title: "update-manager in 10.10 freezes after finishing its work; python script error"
date: 2010-10-18
forum: General Help
---

### Post by Zalbor on 2010-10-18
Whenever update-manager finishes checking for updates or installing them, it stops working with all its widgets disabled. The only way to stop it is to kill the process.
Running it from a terminal produces this output:
```
$ update-manager 
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/UpdateManager/backend/InstallBackendSynaptic.py", line 37, in _on_synaptic_exit
    self.emit("action-done", action)
TypeError: 2 parameters needed for signal action-done; 1 given
```
It looks like a mistake in a python script. I took a look at the file but I don't know what the second parameter is supposed to be. If someone does, this should be an easy thing to fix...

In case this makes a difference (it very well might) I'm using KDE.

---

### Post by Zalbor on 2010-10-21
I added a 0 as the second parameter and it **seems** to work... I just hope it doesn't do something else I probably wouldn't want.

---

