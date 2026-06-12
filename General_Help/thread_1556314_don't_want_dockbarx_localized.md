---
title: "don't want dockbarx localized"
date: 2010-08-19
forum: General Help
---

### Post by daspooky on 2010-08-19
Hello!

I recently installed dockbarx  throught the ppa  ppa:dockbar-main/ppa

I have following locales set up:

LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
LC_CTYPE="nl_BE.UTF-8"
LC_COLLATE="nl_BE.UTF-8"
LC_TIME="nl_BE.UTF-8"
LC_NUMERIC="nl_BE.UTF-8"
LC_MONETARY="nl_BE.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="nl_BE.UTF-8"
LC_NAME="nl_BE.UTF-8"
LC_ADDRESS="nl_BE.UTF-8"
LC_TELEPHONE="nl_BE.UTF-8"
LC_MEASUREMENT="nl_BE.UTF-8"
LC_IDENTIFICATION="nl_BE.UTF-8"

Dockbarx default its menu's to dutch. However I like to have my operating system and software in English.

Is there any way to change the language used by dockbarx?

---

### Post by M7S on 2010-08-19
DockbarX uses pythons locale.getdefaultlocale() that should use the the locale set in environment variable LANGUAGE if I understand the lightly cryptic descriptions here: [http://docs.python.org/library/locale.html#locale.getdefaultlocale](http://docs.python.org/library/locale.html#locale.getdefaultlocale)
If locale.getdefaultlocale() fails it should get the locale from the environment variable LANG directly. If that fails to it should default to en_US. 

The question is why this doesn't work for you. Can you start python from a terminal and run these two commands and post the output:

import locale
locale.getdefaultlanguage()

That might help me solve this bug.

---

### Post by daspooky on 2010-08-20
I'm guessing you mean to execute:
import locale
locale.getdefaultlocale()

which returns: ('nl_BE', 'UTF8')

---

### Post by daspooky on 2010-10-07
Take a look at this bug report for another program with a similar issue:

[http://ubuntuforums.org/showthread.php?t=1556314](http://ubuntuforums.org/showthread.php?t=1556314)

It seems getdefaultlocale searches for the variables in following order:

LC_ALL
LC_CTYPE
LANG

It's looking if LC_ALL is set, if not, it looks for LC_CTYPE, then LANG, and
finally LANGUAGE. If I have a LC_CTYPE defined, it will choose that before
the LANG variable.

A bugfix would then be to ignore the value of LC_CTYPE and determine the interface language by using the LANGUAGE variable.

---

### Post by M7S on 2010-10-07
I forgot to tell you, a supposed fix is released in x.0.38, that hopefully will be in the ppa soon.

---

