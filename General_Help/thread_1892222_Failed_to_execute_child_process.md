---
title: "Failed to execute child process"
date: 2011-12-07
forum: General Help
---

### Post by novateando on 2011-12-07
Hi, 

I would like to know what to do when this message appears when trying to launch an application in Ubuntu 10.04.

In particular, my problem is with Bauble.

me@me-laptop:~$  bauble
Traceback (most recent call last):
  File "/usr/local/bin/bauble", line 4, in <module>
    import pkg_resources
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 2655, in <module>
    working_set.require(__requires__)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 648, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 546, in resolve
    raise DistributionNotFound(req)
pkg_resources.DistributionNotFound: Beaker>=1.1

Thanks for all suggestions

---

### Post by phidia on 2011-12-07
Can you do > sudo apt-get install beaker 
and then try to launch your app if that completes?

---

### Post by novateando on 2011-12-07
Great, it launches now! But only from the terminal. How can I fix the application menu?

Many thanks

---

### Post by novateando on 2011-12-09
I managed it, it was pretty easy in the end.

---

