---
title: "perl: warning: Setting locale failed."
date: 2006-03-01
forum: General Help
---

### Post by event on 2006-03-01
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```
I've been getting this error trolled over and over again whenever I do something with the Kernel, such as update it, or update a driver or something. Is this something to be worried about? How can I fix it?

---

### Post by armware on 2006-12-12
that's a locale setting issue which i am currently fighting with myself. i'm posting this to help point you in the right direction, and maybe you'll find the solution before i do.

---

### Post by armware on 2006-12-12
i fixed mine! here's what i did, i hope it works for you too:

sudo locale-gen
sudo dpkg-reconfigure locales


good luck

---

### Post by gigaferz on 2007-03-10
Thank you  soo much!!!!

---

### Post by gigaferz on 2007-03-10
ahh !! so close,, does anybodyhas a link how to set this locale thing??

Or what is the cause for that??

Is it because i installed  debian packages???

---

### Post by SirYes on 2007-03-20
> **gigaferz said:**
> ahh !! so close,, does anybodyhas a link how to set this locale thing??

Or what is the cause for that??

Is it because i installed  debian packages???

1) Check the definition of LANGUAGE variable in **/etc/environment**
```
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"
```
If it's not there, add something like the above, or specify multiple languages and select one for LANG (here "pl" is for Polish and "fr" is for French)
```
LANGUAGE="pl_PL:pl:fr_FR:fr:en_US:en"
LANG="pl_PL.UTF-8"
```

2) Exactly the same locales (all that are specified in LANGUAGE variable) must be present in **/etc/locale.def**
Make sure to include all variants that you are going to use (UTF-8, @euro, etc.)
```
# This file lists locales that you wish to have built. You can find a list
# of valid supported locales at /usr/share/i18n/SUPPORTED. Other
# combinations are possible, but may not be well tested. If you change
# this file, you need to rerun locale-gen.
#

en_US ISO-8859-1
en_US.ISO-8859-15 ISO-8859-15
en_US.UTF-8 UTF-8
pl_PL ISO-8859-2
pl_PL.UTF-8 UTF-8
fr_FR ISO-8859-1
fr_FR.UTF-8 UTF-8
fr_FR@euro ISO-8859-15
```
3) After these modifications, issue as a root either
```
# locale-gen
```
or:
```
# dpkg-reconfigure locales
```

Final result - NO MORE dreaded message:
> perl: warning: Setting locale failed

:D

---

### Post by gigaferz on 2007-03-20
Thank you!!!

Finally!  it works!!!

---

### Post by SirYes on 2007-03-21
Other threads concerning the same issue:
[LIST]
[*]perl: warning: Setting locale failed - [thread]75493[/thread]
[*]Perl warning: Setting locale failed - [thread]319397[/thread]
[/LIST]

---

### Post by peter_ryan on 2007-11-05
I [blogged about this issue]("http://www.peterryan.net/2007/11/05/perl-locale-is-corrupted-after-gutsy-upgrade/") around the time when I upgraded from feisty to gutsy. The locale-gen and locales reconfiguration resolution steps solved my problem.

---

