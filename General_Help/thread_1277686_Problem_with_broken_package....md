---
title: "Problem with broken package..."
date: 2009-09-28
forum: General Help
---

### Post by YourSurrogateGod on 2009-09-28
```
Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/texmf.cnf with new version

Setting up texlive-common (2007-13ubuntu0.1) ...

Setting up texlive-base-bin (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
	This may take some time... done.

Errors were encountered while processing:
 libghc6-hsql-postgresql-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
$
```
This is kind of annoying.  The above package, libghc6-hsql-postgresql-dev, is busted for some reason.  In Synaptic I tried to remove it, completely remove it or re-install it, to no avail!  Each time that I do something like that I get an error message saying that it is broken and nothing else can be done.  Thoughts?

---

### Post by zvacet on 2009-09-29
```
sudo apt-get -f install
```

---

### Post by YourSurrogateGod on 2009-09-29
> **zvacet said:**
> ```
sudo apt-get -f install
```
I don't think that worked...
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopencdk10-dev libgnutlsxx13 libtasn1-3-dev libgpg-error-dev libgcrypt11-dev libgnutls-dev liblzo2-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libghc6-hsql-postgresql-dev (1.7-1) ...
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/hsql-postgresql-1.7/installed-pkg-config" ... done.
ghc-pkg: /usr/include/postgresql/8.3/server doesn't exist or isn't a directory (use --force to override)
dpkg: error processing libghc6-hsql-postgresql-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libghc6-hsql-postgresql-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by zvacet on 2009-09-29
```
sudo dpkg --configure -a
```

---

### Post by YourSurrogateGod on 2009-09-29
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

Still doesn't work :) .  Maybe I'm doing something very wrong?
```
$ sudo dpkg --configure -a
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libghc6-hsql-postgresql-dev (1.7-1) ...
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/hsql-postgresql-1.7/installed-pkg-config" ... done.
ghc-pkg: /usr/include/postgresql/8.3/server doesn't exist or isn't a directory (use --force to override)
dpkg: error processing libghc6-hsql-postgresql-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libghc6-hsql-postgresql-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by zvacet on 2009-09-30
Run just this one 

```
sudo dpkg --configure -a

```

---

### Post by YourSurrogateGod on 2009-09-30
Yeh, that didn't do it.

---

