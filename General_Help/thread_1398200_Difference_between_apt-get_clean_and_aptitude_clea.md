---
title: "Difference between apt-get clean and aptitude clean"
date: 2010-02-04
forum: General Help
---

### Post by lost. on 2010-02-04
Is there any difference between apt-get clean and aptitude clean? Do they both remove the same caches? Should I know any other commands for cleaning up wasted space on my ubuntu laptop?

---

### Post by audiomick on 2010-02-04
from
```
man apt-get
```
 ```
clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

```

from
```
man aptitude
```
 ```
 clean
           Alle heruntergeladenen und zwischengespeicherten .deb-Dateien aus
           dem Paketcache löschen. Der Paketcache liegt normalerweise unter
           /var/cache/apt/archives.

       autoclean
           Löscht alle zwischengespeicherten Paketdateien, die nicht mehr
           heruntergeladen werden können. Dies verhindert das grenzenlose
           Wachstum des Cacheverzeichnisses, ohne es vollständig zu leeren.

```
oops, that one is in German, sorry.

Anyway, It says effectively the same thing.

---

