---
title: "Can i delete packages in /var/cache/apt/archives ?"
date: 2011-01-12
forum: General Help
---

### Post by aldee96 on 2011-01-12
I really want to free up disk spaces in my ubuntu, so i look up disk analyzer then i saw /var/cache/apt/archives take about 1.2GB space from my disk. can i deleted those packages to free up disk spaces? the packages there is a *.deb files, when i click on some them, it open ubuntu software center. an the ubuntu software center describe the newer upgrade is installed. that's why i wanted to delete them :confused:

---

### Post by moore.bryan on 2011-01-12
```
sudo aptitude clean
```
From the man for aptitude:
> clean
           Removes all previously downloaded .deb files from the package cache directory (usually
           /var/cache/apt/archives).


---

### Post by aldee96 on 2011-01-12
> **moore.bryan said:**
> ```
sudo aptitude clean
```From the man for aptitude:

it's not working by the way i'm using ubuntu 10.10

---

### Post by matt_symes on 2011-01-12
Hi

Try

```
sudo apt-get autoclean
```

from man apt-get

> autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

or 

```
sudo apt-get clean
```

> clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(1) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

Take your pick.

Kind regards

---

### Post by oldos2er on 2011-01-12
> **aldee96 said:**
> it's not working by the way i'm using ubuntu 10.10

*sudo apt-get clean* will accomplish the same task. *aptitude* is available from the repositories.

---

### Post by A_M_S on 2011-01-12
Sometimes you can free some disk space with

```

sudo apt-get autoremove

```

From the man apt-get:
> autotoremove is used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed.

---

