---
title: "unhandable error occured (key error: 'libdua5.1-wsapi-fcgi-dev'?)"
date: 2011-02-01
forum: General Help
---

### Post by uniqueone-85 on 2011-02-01
hi i'm am still pretty new to ubuntu and i am currently having trouble  installing software from the software center and using update manager.  when ever i try to install a new program i get the following error  message:

There seems to be a programming error in aptdaemon, the software that  allows you to install/remove software and to perform other package  management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

the details are this:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 179, in _process_transaction
    self.commit_packages(*self.trans.packages)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 227, in commit_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 726, in _commit_changes
    self._check_obsoleted_dependencies()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 518, in _check_obsoleted_dependencies
    for pkg in self._cache:
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 173, in __iter__
    yield self[pkgname]
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 158, in __getitem__
    pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: 'libdua5.1-wsapi-fcgi-dev'

when ever i run update manager thru terminal i am presented with this same message as above. 

I'm am currently using ubuntu 11.04, but i originally installed 10.10. i  now realize that the version i am currently using is for developers and  there may be no immediate fix, but i have no idea how i upgraded or  stop it from automatically upgrading to alpha builds. 

Any help will be greatly appreciated.

---

### Post by uniqueone-85 on 2011-02-01
also when ever i open update manager in administration it comes up and closes as soon as building data structures is loaded.

---

