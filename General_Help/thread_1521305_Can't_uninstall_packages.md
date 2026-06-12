---
title: "Can't uninstall packages"
date: 2010-06-30
forum: General Help
---

### Post by noper2 on 2010-06-30
For some reason, whenever running any apt-get command, I receive the following error:
```
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libt1-5 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing texlive-extra-utils ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing texlive-extra-utils (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing texlive-font-utils ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing texlive-font-utils (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 libt1-5
 texlive-extra-utils
 texlive-font-utils

```
I've tried many times to uninstall these packages but they won't leave! Any advice?

---

### Post by dabl on 2010-06-30
Try one of them like this:

```
sudo dpkg --force all --remove libt1-5
```

If that works, you can do the same to the others.

---

### Post by noper2 on 2010-07-04
> **dabl said:**
> Try one of them like this:

```
sudo dpkg --force all --remove libt1-5
```

If that works, you can do the same to the others.

I tried that, and I just get this message:

```
$ sudo dpkg --force all --remove libt1-5
(Reading database ... 156810 files and directories currently installed.)
Removing libt1-5 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libt1-5 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libt1-5

```

Any other suggestions?

---

### Post by noper2 on 2010-07-10
I've solved this problem, in case anyone else is looking for help with it. The solution can be found here:
[http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html]("http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html")

The only step you need to change is putting an "!" after the "#" in the line "#/bin/sh", that is:
```
#!/bin/sh
```

Good luck!

---

### Post by WorMzy on 2010-07-10
Edit: never mind. You got it. :)

---

