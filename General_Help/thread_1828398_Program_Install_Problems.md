---
title: "Program Install Problems"
date: 2011-08-18
forum: General Help
---

### Post by Caleb Gorde on 2011-08-18
Hello, when I attempt to install any program from the Ubuntu Software Center, it begins the installation and gives me this error


     There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

Any idea how to help me?

---

### Post by jfed on 2011-08-18
This just may help, try it out.

[http://ubuntuforums.org/showthread.php?t=1610154](http://ubuntuforums.org/showthread.php?t=1610154)

Even if it doesn't, reading is good for you! :D

---

### Post by Caleb Gorde on 2011-08-18
Thanks for the reply it helped me!

---

### Post by jfed on 2011-08-18
Oh really? Wow I didn't even think it would help that much, haha. Cool, glad to help :D

---

### Post by Caleb Gorde on 2011-08-19
Ha yeah it was just a broken Java Package.

---

