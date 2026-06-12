---
title: "Understanding apt-get - or - &quot;...but it is not going to be installed&quot;?"
date: 2011-11-10
forum: General Help
---

### Post by msp3k on 2011-11-10
Stupid apt-get question:

I recently tried an experiment:

1) After making a basic install from the 11.04 server disk, I used dpkg-query --show to make a list of all the installed packages, along with their versions.

2) Installed ubuntu-desktop

3) Decided to try installing gnome3 from the ppa

4) Now this is where it gets hairy, I decided to try taking the machine back to it's state after step 2.  I did this by:

4a) Removing all packages that were not listed in my output of dpkg-query --show from step 1.  (I.e., back to the basic server installation.)

4b) Deleting all packages in /var/cache/apt/archives/

4c) Removing the gnome3 ppa from /etc/apt/sources.list.d/

4d) apt-get update ; apt-get install ubuntu-desktop

I thought that this would do it, but apparently not.  I ran into a couple of problems:

Problem #1) There was one package where apt-get still thought it needed to get the version from the ppa rather than the version from the main repositories.  After deleting the packages from the cache directory, removing the uri's for the ppa, and doing an apt-get update, I thought that this would not happen.  Although I was able to fix it by specifying the required version, I would like to understand why apt-get still thought that it needed the ppa version.

Problem #2) While installing ubuntu-desktop, I see a lot of errors from apt-get that read something like: <package> : Depends: <some-other-package> (<version>) but it is not going to be installed

Ex:

```
 unity : Depends: libbamf0 (>= 0.2.60) but it is not going to be installed
         Depends: libdee-1.0-1 (>= 0.5.2) but it is not going to be installed
         Depends: libunity-misc0 (>= 0.2.1) but it is not going to be installed
         Depends: compiz but it is not going to be installed
         Depends: compiz-core but it is not going to be installed
         Depends: compiz-core-abiversion-20110322
         Depends: compiz-plugins-main but it is not going to be installed
         Depends: libglib2.0-bin but it is not going to be installed
         Depends: unity-asset-pool (>= 0.8.18) but it is not going to be install
```

Forgive me for being dense, but isn't it apt-get's job to reconcile dependencies and install these required packages?  Obviously this is how it worked the first time, when going from steps (1) to (2), but this isn't the way that it works now.

This is a test machine, so it's not critical, but I would like to understand what's going on here.

---

### Post by msp3k on 2011-11-10
While I still don't understand what's going on inside apt-get, I believe I have found the solution: Don't remove the ppa by deleting the gnome3 uri file from /etc/apt/source.list.d/ and doing an apt-get update, but rather install ppa-purge and use that to remove the ppa.  In addition to removing the ppa uri file from sources.list.d/, ppa-purge will also remove the packages installed from the ppa.

---

