---
title: "Unable to install programs"
date: 2011-11-20
forum: General Help
---

### Post by impelus on 2011-11-20
I searched the forum and see that others have the same problem, but even their issues have been solved, I can't figure out how to go about solving it myself.

The error I get is as follows:

An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.
```

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the libstdc++6-4.6-dev package. This might mean you need to manually fix this package.

```

Someone said they fixed it by uninstalling and reinstalling the software center, but I cannot figure out how to do that. 

Any help would be appreciated. Thanks

---

### Post by hansdown on 2011-11-20
Hi, impelus.

Is this an upgrade?

There seem to be, a number of launchpad entries, for this.

Not sure, of a fix.

---

### Post by raja.genupula on 2011-11-20
Hi man 
open your synaptic and try to reinstall this package 
```
libstdc++6-4.6-dev
```

and try again
all the best

---

### Post by impelus on 2011-11-20
Actually, synaptic wasn't even installed. I had to install it

```
sudo apt-get install synaptic
```

*This wasn't an upgrade. It was a clean install via wubi.

Thanks for the help.

---

### Post by hansdown on 2011-11-20
> **impelus said:**
> Actually, synaptic wasn't even installed. I had to install it

```
sudo apt-get install synaptic
```

*This wasn't an upgrade. It was a clean install via wubi.

Thanks for the help.

I keep forgetting, synaptic needs to be installed.

Glad you fixed it,impelus.

---

