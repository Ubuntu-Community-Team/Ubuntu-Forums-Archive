---
title: "64bit java-common error on LUCID upgrade"
date: 2010-05-17
forum: General Help
---

### Post by metadrop on 2010-05-17
I have tried reinstalling, upgrading and removing and overwriting.. not sure what to do from here...


```
$ sudo dpkg --force-all -r java-common
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 258897 files and directories currently installed.)
Removing java-common ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing java-common (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 java-common
```

---

