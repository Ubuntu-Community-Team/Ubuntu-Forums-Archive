---
title: "update fatal error"
date: 2010-12-01
forum: General Help
---

### Post by DarkBeer on 2010-12-01
I am trying to apply updates, but receiving the following error:

```
Fetched 110MB in 14min 19s (128kB/s)                                                                                                  
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 65%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libopenmpi-dev': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

This was during at apt-get upgrade command that I tried after apt-get clean and apt-get update.  I receive the same error if I try apt-get -f install.

I would appreciate any suggestions on getting around this error so I can catch up the 61 updates that are waiting.

---

### Post by DarkBeer on 2010-12-03
No ideas?

---

### Post by Spyderkid on 2010-12-03
I'm not sure but it says that this file it wants to install is a directory, i'm not sure what to do exsept try again and maybe issue the command 

```

sudo apt-get clean

```

to get rid of any caches before re-installing the updates

---

### Post by sikander3786 on 2010-12-03
libopenmpi-dev seems to be causing problems here.

Try removing and re-installing that package.

```
sudo dpkg --purge --force all libopenmpi-dev
```

```
sudo rm /var/cache/apt/archives/*
```

```
sudo apt-get update && sudo apt-get install libopenmpi-dev
```


If that doesn't solve the problem, try renaming your existing libopenmpi-dev by,

```
sudo mv /var/lib/dpkg/info/libopenmpi-dev /var/lib/dpkg/info/libopenmpi-dev.old
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by DarkBeer on 2010-12-03
First option resulted in:

```
dpkg --purge --force all libopenmpi-dev
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 65%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libopenmpi-dev': Is a directory
```

After moving to .old, the update/upgrade resulted in:

```
61 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
5 not fully installed or removed.
Need to get 23.1MB/110MB of archives.
After this operation, 10.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-beta 8.0.552.215-r67652 [23.1MB]
Fetched 23.1MB in 9s (2,480kB/s)                                                                                                      
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 65%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libopenmpi-dev': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Is there a possible problem with a file list?

---

### Post by DarkBeer on 2010-12-03
Finally figured out the problem.  In /var/lib/dpkg/info I had libopenmpi-dev.list and libopenmpi-dev.list-new.  Did a rmdir on the .list file, then mv the -new to libopenmpi-dev.list.  Tried to upgrade, but failed on a new file at that point.  Did a ls -l *-new in the /var/lib/dpkg/info dir and found 5 additional instances with -new files.  Repeated the process above of doing a rmdir on the list, then mv the -new to .list and then was able to complete the upgrade.

---

