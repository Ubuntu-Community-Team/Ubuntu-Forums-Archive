---
title: "go back to stable version of firefox from beta version"
date: 2010-02-14
forum: General Help
---

### Post by john2938 on 2010-02-14
In ubuntu 9.04, I tried to upgrade from firefox 3.0 to 3.5, by  installing some apt-get packages, and there is a problem! Now firefox  calls itself "Namoroka" and the firefox logo is gone and replaced by a  black square in the upper bar and it says it is a development beta  version. I really don't like this version, how can I go back to the  stable version of firefox? I tried apt-get remove firefox-3.5 and  apt-get install firefox-3.0 and that did not work. How do I go back to  the stable version of firefox?

---

### Post by cdawley4 on 2010-02-14
Hi,

Welcome to the forums.  There is lots to be learned with this software.  I am still learning myself.  I had something similar to that once.  I am going to post a link to my thread in here.  It may or may not help.  There should be lots of posts here in the forum about rolling back to your previous version of firefox.

[http://ubuntuforums.org/showthread.php?t=1194623](http://ubuntuforums.org/showthread.php?t=1194623)

Hope that helps.

---

### Post by lovinglinux on 2010-02-14
Open "System >> Administration >> Software Sources", go to the Other Software tab and locate an entry with *ubuntu-mozilla-daily* then disable it and hit the Close button then Reload in the prompted window. Then open a terminal "Application >> Acessories >> Terminal" and run these commands:

```
sudo apt-get remove firefox-3.5
```
```
sudo apt-get --reinstall install firefox firefox-3.0
```

If you don't have anything similar to *ubuntu-mozilla-daily* in your Software Sources, then I will need more info on how you installed it.

A little advice...don't run commands or add repositories without knowing what they do. Additionally, is a good practice to annotate any changes you make that use software sources outside the official repositories, so you can roll-back if you want.

---

### Post by lovinglinux on 2010-02-14
[See my previous post for a fix]

BTW, if you want to install the latest Firefox with proper logo and branding and you have a 32bit Ubuntu, then use Ubuntuzilla repository. See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

