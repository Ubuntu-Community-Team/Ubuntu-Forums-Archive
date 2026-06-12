---
title: "maintainers, please update libtiff-tools"
date: 2010-09-21
forum: General Help
---

### Post by duane-tech on 2010-09-21
To (k)ubuntu maintainers, 

Please update Hardy's libtiff-tools from 3.8.2 to 3.9.4. All the older version's tools (except tiffdump) crash when operating on larger (>2GB) tiff files. The problem is fixed in the newest version of libtiff.

This is particularly annoying when using tiffsplit, for which there are few alternatives and the files tend to be large.

---

### Post by lloyd_b on 2010-09-22
> **duane-tech said:**
> To (k)ubuntu maintainers, 

Please update Hardy's libtiff-tools from 3.8.2 to 3.9.4. All the older version's tools (except tiffdump) crash when operating on larger (>2GB) tiff files. The problem is fixed in the newest version of libtiff.

This is particularly annoying when using tiffsplit, for which there are few alternatives and the files tend to be large.
Due to some decisions made by the Kubuntu developers, Kubuntu Hardy is *not* an LTS (long term support) release (Ubuntu and Xubuntu Hardy *are* LTS versions, but not Kubuntu Hardy).  This means it's not guaranteed to be updated for 3 years like an LTS release.

As such, I wouldn't hold my breath waiting for them to update it.

You should seriously consider updating to Kubuntu Lucid, which *is* an LTS release, and will be maintained for 3 years.

Lloyd B.

---

### Post by duane-tech on 2010-09-23
Yeah, I guess Ubuntu doesn't want to support KDE 3 when the development team for that project has moved on to KDE 4.x, but the rest of the system, including libtiff, is shared between the different flavors of Hardy, which are LTS'ed.

I found a solution, I upgraded to libtiff-tools_3.8.2-13ubuntu0.3_amd64.deb which is found in karmic-updates.
That version fixed the problem as described in the Ubuntu Changelog:

> tiff (3.8.2-13) unstable; urgency=high

  * Apply patches to fix CVE-2009-2347, which covers two integer overflow
    conditions.
  * LZW patch from last update addressed CVE-2009-2285.  Renamed the patch
    to make this clearer.

 -- Jay Berkenbilt <qjb@debian.org>  Sun, 12 Jul 2009 18:03:33 -0400


Backporting this solution to Hardy would be trivial as it doesn't require any other package upgrades.

---

