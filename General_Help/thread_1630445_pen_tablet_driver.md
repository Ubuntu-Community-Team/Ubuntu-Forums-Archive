---
title: "pen tablet driver"
date: 2010-11-25
forum: General Help
---

### Post by _linux_newbie_ on 2010-11-25
Hello :D !

Trying to set up wizard pen driver from this tutorial:
_[https://help.ubuntu.com/community/TabletSetupWizardpen#I%20have%20problems%20not%20solved%20by%20the%20above%20troubleshooting](https://help.ubuntu.com/community/TabletSetupWizardpen#I%20have%20problems%20not%20solved%20by%20the%20above%20troubleshooting)_

All goes well, but when I do the "make && sudo make install" commands, there is an error

I am on Ubuntu 10.10.

Please help : 

```
make  all-recursive
make[1]: Entering directory `/home/administrator/Documents/WizardpenDriver/xorg-input-wizardpen-0.8.0'
Making all in src
make[2]: Entering directory `/home/administrator/Documents/WizardpenDriver/xorg-input-wizardpen-0.8.0/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
libtool: Version mismatch error.  This is libtool 2.2.6 Debian-2.2.6a-4, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.6 Debian-2.2.6a-4
libtool: and run autoconf again.
make[2]: *** [wizardpen.lo] Error 63
make[2]: Leaving directory `/home/administrator/Documents/WizardpenDriver/xorg-input-wizardpen-0.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/administrator/Documents/WizardpenDriver/xorg-input-wizardpen-0.8.0'
make: *** [all] Error 2

```Thanks,
:D

---

### Post by Favux on 2010-11-25
Hi _linux_newbie_,

Welcome to Ubunut forums.

What tablet do you have?:
```
xinput --list
```
If it is a tablet that uses the WizardPen driver try Martin Owens' ppa for his Maverick driver:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick)

---

