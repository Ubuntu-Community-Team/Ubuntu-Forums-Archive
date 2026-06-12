---
title: "cannot update gzip 1.3.12-8ubuntu1 to 1.1"
date: 2010-03-06
forum: General Help
---

### Post by Walter Bux on 2010-03-06
Hi,

I have weird problem that I couldn't find anything about on the internet: When I try to do the said update in Karmic, I get this error:

Preparing to replace gzip 1.3.12-8ubuntu1 (using .../gzip_1.3.12-8ubuntu1.1_amd64.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gzip_1.3.12-8ubuntu1.1_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.12-8ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Upgrading other packages however works fine. What can be the cause of this? How can I fix it?

Btw: I already reported this as a bug, but no reactions so far.

[https://bugs.launchpad.net/bugs/515658](https://bugs.launchpad.net/bugs/515658)

Many thanks!

---

### Post by dcstar on 2010-03-06
> **Walter Bux said:**
> Hi,

I have weird problem that I couldn't find anything about on the internet: When I try to do the said update in Karmic, I get this error:

Preparing to replace gzip 1.3.12-8ubuntu1 (using .../gzip_1.3.12-8ubuntu1.1_amd64.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gzip_1.3.12-8ubuntu1.1_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.12-8ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Upgrading other packages however works fine. What can be the cause of this? How can I fix it?
.........


Delete the probably corrupted package from your /var/cache/apt/archives folder and go through the install process again.

There is nothing wrong at all with that package, I just reinstalled it on my system.

---

### Post by Walter Bux on 2010-03-07
I have my system configured so it doesn't keep a package archive, i.e. I cannot delete any corrupted package because it is not there.

---

