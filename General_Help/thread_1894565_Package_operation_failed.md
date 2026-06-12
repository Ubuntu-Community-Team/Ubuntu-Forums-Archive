---
title: "Package operation failed"
date: 2011-12-12
forum: General Help
---

### Post by mindaslab on 2011-12-12
Today Ubuntu prompted me for updates, when I clicked install, this happened:

Package operation failed

The installation or removal of a software package failed.

installArchives() failed: perl: warning: Setting locale failed.

perl: warning: Please check that your locale settings:

	LANGUAGE = (unset),

	LC_ALL = (unset),

	LANG = "en_IN.ISO8859-1"

    are supported and installed on your system.

perl: warning: Falling back to the standard locale ("C").

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

perl: warning: Setting locale failed.

perl: warning: Please check that your locale settings:

	LANGUAGE = (unset),

	LC_ALL = (unset),

	LANG = "en_IN.ISO8859-1"

    are supported and installed on your system.

perl: warning: Falling back to the standard locale ("C").

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

perl: warning: Setting locale failed.

perl: warning: Please check that your locale settings:

	LANGUAGE = (unset),

	LC_ALL = (unset),

	LANG = "en_IN.ISO8859-1"

    are supported and installed on your system.

perl: warning: Falling back to the standard locale ("C").

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

(Reading database ... 

dpkg: warning: files list file for package `evolution-indicator' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `libatkmm-1.6-1' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `libxcursor1' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `python-httplib2' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `libnm-glib-vpn1' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `libglewmx1.5' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `gnome-system-tools' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `libvisual-0.4-0' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `libubuntuone1.0-cil' missing, assuming package has no files currently installed.



dpkg: warning: files list file for package `python-argparse' missing, assuming package has no files currently installed.



Can't make a head or tail :-( Please help!

---

### Post by RealityMaster on 2011-12-12
Looks like a similar problem to one I had.


```
sudo locale-gen en_US.UTF-8

```

worked for me

---

