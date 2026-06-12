---
title: "Uninstall Firefox/Chromium"
date: 2011-06-19
forum: General Help
---

### Post by gjw0 on 2011-06-19
I cannot uninstall Firefox, nor can I uninstall Chromium; one always stays if the other is uninstalled.
For example, if I remove Firefox, Chromium will appear in its place and vice versa.
This has got to be one of the weirdest bugs I've ever seen on Ubuntu!
So, how can I uninstall both web browsers?

---

### Post by whatthefunk on 2011-06-19
Hmmm...that is weird.  How have you been unistalling them?  Through the package manager or the terminal?

---

### Post by gjw0 on 2011-06-19
> **whatthefunk said:**
> Through the package manager or the terminal?

Both ways and none worked.

Here's the terminal log:

For Firefox

> :~$ sudo apt-get remove firefox
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
The following packages will be REMOVED:
  firefox firefox-globalmenu
The following NEW packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 0 B/18.6 MB of archives.
After this operation, 46.1 MB of additional disk space will be used.


For Chromium

> :~$ sudo apt-get remove chromium
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'chromium' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by gandaran on 2011-06-19
try
```
sudo apt-get --purge remove chromium-browser
```
should be chromium-browser not just chromium

---

### Post by lovinglinux on 2011-06-19
It is not a bug. You need at least one browser installed, so when you remove one, the other is installed.

Just leave one of them installed. It won't hurt your system and won't take too much space.

---

### Post by pfeoora on 2011-06-20
this worked for me:
```
sudo apt-get --purge remove chromium-browser firefox epiphany-browser midori
```
Now I'm using google chrome... this dependencies crap is big bs in my eyes... I do not want to be told what browser I should use (instead of Firefox) and if I don't want any that's my decision, not Ubuntu's/Canonical's/whoeverelse's
:roll:

---

### Post by bodhi.zazen on 2011-06-20
> **pfeoora said:**
> this worked for me:
```
sudo apt-get --purge remove chromium-browser firefox epiphany-browser midori
```Now I'm using google chrome... this dependencies crap is big bs in my eyes... I do not want to be told what browser I should use (instead of Firefox) and if I don't want any that's my decision, not Ubuntu's/Canonical's/whoeverelse's
:roll:

This is why, IMO, it is easier to perform a minimal install and add only what you want rather then start with a default Ubuntu install and try to start removing things.

---

