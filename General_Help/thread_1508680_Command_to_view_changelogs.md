---
title: "Command to view changelogs?"
date: 2010-06-13
forum: General Help
---

### Post by x-shaney-x on 2010-06-13
Basically, is there a terminal command to view the changelog of a particular package?
I'm sure there was one I used in the past, preferably on the package name itself rather than the deb file.

Manually extracting the deb then poking in there or browsing to the changes.gz file is a bit long-winded.

---

### Post by mc4man on 2010-06-13
you can use aptitude - at simplest something like this, Ex. totem - 

aptitude changelog totem

from man
> changelog
Downloads and displays the Debian changelog for each of the given
source or binary packages.

By default, the changelog for the version which would be installed
with "aptitude install" is downloaded. You can select a particular
version of a package by appending =<version> to the package name;
you can select the version from a particular archive by appending
/<archive> to the package name.


Whether there is an apt* command not sure, never looked for..

---

### Post by x-shaney-x on 2010-06-13
Thanks. Useful but doesn't show changelogs from unofficial packages (such as from a PPA).

---

