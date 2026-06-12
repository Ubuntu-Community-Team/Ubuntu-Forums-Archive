---
title: "/etc/default/locale settings ignored"
date: 2011-06-10
forum: General Help
---

### Post by guygriffiths on 2011-06-10
I am using Kubuntu 11.04, and have set up the correct locale information in /etc/default/locale - it reads:

LANG="en_GB.UTF-8"
LANGUAGE="en_GB"
LC_MESSAGES="en_GB.UTF-8"

which is exactly what I want.  The same lines are also contained in /etc/environment.  However, when I run "locale", I get:

LANG=
LANGUAGE=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME=en_GB
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

i.e. the language settings seem to be being ignored.  This is causing problems with some code compilation - obviously I can set the variables by hand after every boot, but this is not a practical solution.  If anyone has any solutions, I'd be most grateful.

---

