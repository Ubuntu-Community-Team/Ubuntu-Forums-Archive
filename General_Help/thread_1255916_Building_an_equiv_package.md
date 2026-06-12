---
title: "Building an equiv package"
date: 2009-09-02
forum: General Help
---

### Post by mdwrigh2 on 2009-09-02
Basically, here's the gist of my issue:

I've compiled my own version of MySQL with some Sphinx magic sprinkled in it. However, because its compiled from source and not installed from any package management system, anything that requires mysql-common still wants to the package manager to install it. For dpkg the solution to this problem seems to be equiv packages. I've created an equiv package with equiv-control and equiv-build and it appears to build fine, but I can't get it to actually think I've  already installed the mysql-common package. Everything that depends on that package still wants to install it from the repo. 

Below I've attached the document I'm using to build the .deb with equiv-build. Can you see any problems with this? Any suggestions on possible fixes? Or even alternative solutions to my problem would be welcome.
```

Package: mysql-common-sphinx
Version: 1.0
Maintainer: Michael Wright <email address hidden>
# Pre-Depends: <comma-separated list of packages>
# Depends: <comma-separated list of packages>
# Recommends: <comma-separated list of packages>
# Suggests: <comma-separated list of packages>
Provides: mysql-common
Replaces: mysql-common
Conflicts: mysql-common
# Architecture: all
# Copyright: <copyright file; defaults to GPL2>
# Changelog: <changelog file; defaults to a generic changelog>
# Readme: <README.Debian file; defaults to a generic one>
# Extra-Files: <comma-separated list of additional files for the doc directory>
Description: mysql-sphinx package
  mysql-sphinx package
```

---

