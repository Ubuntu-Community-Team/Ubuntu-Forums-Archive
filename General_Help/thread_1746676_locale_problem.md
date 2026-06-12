---
title: "locale problem"
date: 2011-05-02
forum: General Help
---

### Post by wolfen69 on 2011-05-02
When I open Ubuntu Software Center I am told it needs to do a repair, then spits out the following.
```
installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "None.None"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "None.None"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "None.None"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 164992 files and directories currently installed.)
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.0.0-1~~build1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-accessibility-themes 3.0.0-0ubuntu1~build2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_amd64.deb
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-themes-standard (>= 2.91); however:
  Package gnome-themes-standard is not installed.
dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured

```
Any ideas?

---

### Post by ~Plue on 2011-05-02
see if re/installing the language packs fixes it 
```
sudo apt-get install language-pack-en-base
```if it doesn't, you could generate the locales and manually set the variables in in /etc/environment

---

### Post by wolfen69 on 2011-05-02
Thanks for the reply, but I found out my locale was fine, and it was just a bug that the gnome 3 team knew about. It was fixed after an update last night.

---

