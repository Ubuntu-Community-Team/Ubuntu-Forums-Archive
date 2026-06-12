---
title: "Ubuntu-tweak install coruppted"
date: 2009-09-17
forum: General Help
---

### Post by wildman4god on 2009-09-17
I was setting up a new ubuntu install and I installed ubuntu tweak so I could easily enable new repos, the program installed and it works but I keep getting an error and now it as hung up apt so I can install or remove software, I need to know how to remove the coruptd ubuntu-tweak so I can get back to normal operations. I googled the problem and I found a solution but it didn't work for me.
Here is the error I get:

```
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
```

does anyone know what to do?

---

### Post by Partyboi2 on 2009-09-18
Hi, open a terminal and try
```
sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak
```

---

### Post by wildman4god on 2009-09-18
It returned this error:

```
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 157716 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
```

---

### Post by bfleege on 2009-09-18
Go check out my post from a near-identical thread (below).  I outlined a procedure that worked for me.

[http://ubuntuforums.org/showpost.php?p=7966349&postcount=34]("http://ubuntuforums.org/showpost.php?p=7966349&postcount=34")

---

### Post by wildman4god on 2009-09-18
> **bfleege said:**
> Go check out my post from a near-identical thread (below).  I outlined a procedure that worked for me.

[http://ubuntuforums.org/showpost.php?p=7966349&postcount=34]("http://ubuntuforums.org/showpost.php?p=7966349&postcount=34")

Thank you, it worked, though I found my problem, you were right I accidentally install Ubuntu tweak for karmic not jaunty, my bad.

Thanks again.

---

