---
title: "system crashed while installing a package..."
date: 2010-03-17
forum: General Help
---

### Post by xinix on 2010-03-17
for some reason my system crashed while installing a package.  Now I get this error every time I install/remove a package.  I have tried re-installing, removing, forcing options, 'dpkg --configure -a', dpkg-reconfigure.  Nothing has worked.

```
Setting up mpg123 (1.7.3-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec f$
dpkg: error processing mpg123 (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mpg123
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

what do I need to do to fix this?

Thanks

---

### Post by Penguin Guy on 2010-03-17
You could try removing the broken package: [FONT="Courier New"]sudo apt-get purge mpg123[/FONT]

---

### Post by xinix on 2010-03-18
I tried purging it wouldn't work either.

---

