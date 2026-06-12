---
title: "Firefox update locked out"
date: 2006-06-03
forum: General Help
---

### Post by fragos on 2006-06-03
I looked in Firefox about:config and found that Firefox update is locked out.  When will we get new security updates, 1.5.0.4 was released by Mozilla?  Why is Firefox disabled this way?

---

### Post by eystman on 2006-06-03
[Try this. ]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28new%29")

---

### Post by aysiu on 2006-06-03
[QUOTE=eystman][Try this. ]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28new%29")[/QUOTE] Or, better yet, [this](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).

---

### Post by tsb on 2006-06-03
I stuck with the Ubuntu repo version of FF personally.  The fonts are much, much better than the mozilla build on my KDE system.

aysiu - Make sure you tell KDE users to install the dependencies when they install mozilla's FF.  You can select them easily by choosing to install FF in Adept but then deselcting FF and leaving the dependencies.

---

### Post by aysiu on 2006-06-03
[QUOTE=tsb]
aysiu - Make sure you tell KDE users to install the dependencies when they install mozilla's FF.  You can select them easily by choosing to install FF in Adept but then deselcting FF and leaving the dependencies.[/QUOTE] That script installs the Ubuntu Firefox first.

---

### Post by OffHand on 2006-06-03
Nice script Aysiu. Thanks.

---

### Post by aysiu on 2006-06-03
[QUOTE=subsonic_shadow]Nice script Aysiu. Thanks.[/QUOTE] Thank nanotube, who did most of the work.

---

### Post by DarthGroznii on 2006-06-03
[QUOTE=aysiu]Thank nanotube, who did most of the work.[/QUOTE]

Neither script for Firefox or Thunderbird is working for me - I'm getting the following errors:

> 
Backing up old Firefox preferences

cp: cannot stat `/home/christian/.mozilla_backup/.mozilla/firefox/profiles.ini': Permission denied
cp: cannot stat `/home/christian/.mozilla_backup/.mozilla/firefox/xlg1l59r.default': Permission denied
cp: cannot stat `/home/christian/.mozilla_backup/.mozilla/firefox/pluginreg.dat': Permission denied
cp: cannot create regular file `/home/christian/.mozilla_backup/.mozilla/appreg': Permission denied
Previous command did not complete successfully. Exiting.


And Thunderbird....

> 
Backing up old thunderbird preferences

cp: cannot open `/home/christian/.mozilla-thunderbird/inohdwq8.default/cookies.txt' for reading: Permission denied
Previous command did not complete successfully. Exiting.


Please advise, or am I going to have to do it the hard way?

---

### Post by aysiu on 2006-06-03
It sounds as if, for some strange reason, you don't have access to files and folders in your own /home folder.

Try this command: ```
sudo chown -R christian:christian /home/christian
``` Then run both scripts.

---

