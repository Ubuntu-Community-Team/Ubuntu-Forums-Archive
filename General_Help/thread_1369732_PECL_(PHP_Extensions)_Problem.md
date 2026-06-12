---
title: "PECL (PHP Extensions) Problem"
date: 2010-01-01
forum: General Help
---

### Post by Kerubu on 2010-01-01
Hi,

I'm trying to install Cairo for PHP using PECL, but the installation fails :

> sudo pecl install cairo-0.1.0
downloading Cairo-0.1.0.tgz ...
Starting to download Cairo-0.1.0.tgz (117,801 bytes)
..........................done: 117,801 bytes
19 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
configure.in:158: warning: LTOPTIONS_VERSION is m4_require'd but not m4_defun'd
aclocal.m4:2943: LT_INIT is expanded from...
aclocal.m4:2978: AC_PROG_LIBTOOL is expanded from...
configure.in:158: the top level
configure.in:158: warning: LTSUGAR_VERSION is m4_require'd but not m4_defun'd
configure.in:158: warning: LTVERSION_VERSION is m4_require'd but not m4_defun'd
configure.in:158: warning: LTOBSOLETE_VERSION is m4_require'd but not m4_defun'd
configure:4778: error: possibly undefined macro: m4_ifval
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:7557: error: possibly undefined macro: _LT_SET_OPTIONS
configure:7557: error: possibly undefined macro: LT_INIT
ERROR: `phpize' failed


I'm not too sure what's wrong, possibly 'libtool' problem, but anyone got any ideas ?

Thanks

---

