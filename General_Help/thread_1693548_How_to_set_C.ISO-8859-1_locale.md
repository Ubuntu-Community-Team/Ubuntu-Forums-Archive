---
title: "How to set C.ISO-8859-1 locale?"
date: 2011-02-23
forum: General Help
---

### Post by befeleme on 2011-02-23
Hi all,
in order to run Actel's Libero, I need to set my locale to C.ISO-8859-1. I tried simply
```

$ export LANG=C.ISO-8859-1
$ sudo dpkg-reconfigure locales

```and got

```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "C.ISO-8859-1"
    are supported and installed on your system.

``````

$ locale-gen C.ISO-8859-1

```runs through, but does not generate anything.

Installed locales are as follows:

```

$ locale -a

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
cs_CZ.utf8
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
fr_FR.utf8

```It seems only "C" locale is present, however, required "C.ISO-8859.1" isn't. Can anybody advice me how to set (possibly install) C.ISO-8859-1?

---

