---
title: "Google Chrome stable downgrade, please help to find deb package"
date: 2011-12-08
forum: General Help
---

### Post by starlinq on 2011-12-08
Hi,

I have Ubuntu 11.04 Natty 32 bit, and recently upgraded google-chrome-stable package to version 15. However, it constantly crashes on one of my computers, so I want to downgrade it to previous version 14.

It is ridiculous ... but Google does not keep any download archive of its versions so all links to google download server will give the newest version (currently is something like 15.0.874.121). I really regret not keeping the version 14.

Could anyone help me to get previous version 14 of google-chrome-stable deb package?

Thank you in advance.

starlinq

---

### Post by phidia on 2011-12-08
There is a [site here]("http://www.oldapps.com/google_chrome.php") that looks promising.

---

### Post by mc4man on 2011-12-08
if this was your 2nd or greater update then browse in nautilus to /var/cache/apt/archives & see if the older version is there or look in your Downloads folder

If it's  in /var/cache/apt/archives then you can probably force the version back in synaptic > search goggle-chrome > highlight the package > edit > force version

Otherwise or if in Downloads then  use dpkg, as in 
sudo dpkg -i /path/to/name-of.deb

---

### Post by starlinq on 2011-12-08
> **phidia said:**
> There is a [site here]("http://www.oldapps.com/google_chrome.php") that looks promising.

Thank you for your response ... unfortunately :( the site has old Google Chrome versions only for Windows.

---

### Post by phidia on 2011-12-08
> **starlinq said:**
> Thank you for your response ... unfortunately :( the site has old Google Chrome versions only for Windows.

Sorry :(

---

### Post by starlinq on 2011-12-08
> **mc4man said:**
> if this was your 2nd or greater update then browse in nautilus to /var/cache/apt/archives & see if the older version is there or look in your Downloads folder

If it's  in /var/cache/apt/archives then you can probably force the version back in synaptic > search goggle-chrome > highlight the package > edit > force version

Otherwise or if in Downloads then  use dpkg, as in 
sudo dpkg -i /path/to/name-of.deb

Thank you. I checked my cache archive and found the following version: google-chrome-stable_15.0.874.121-r109964_i386.deb unfortunately that is my currently installed version. Just wish, it would be nice if the archive could keep at least 2 versions down. In Downloads folder, I have found version 13. If I cannot find the version 14, will go to the 13th.

---

### Post by mc4man on 2011-12-08
If you get hung up I always copy out things like this (tend to do alot of re-installs when testing) so have this, guess it could be uploaded to mediafire or maybe ubuntuone

> Package: google-chrome-stable
Version: 14.0.835.202-r103287
Architecture: i386
Maintainer: Chrome Linux Team <chromium-dev@chromium.org>
Installed-Size: 105340

---

### Post by oldtimer7777 on 2011-12-09
Did you install Chrome from the PPA? 

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about 1/4th the way down the checklist. No crashes on my system with it.

> **starlinq said:**
> Hi,

I have Ubuntu 11.04 Natty 32 bit, and recently upgraded google-chrome-stable package to version 15. However, it constantly crashes on one of my computers, so I want to downgrade it to previous version 14.

It is ridiculous ... but Google does not keep any download archive of its versions so all links to google download server will give the newest version (currently is something like 15.0.874.121). I really regret not keeping the version 14.

Could anyone help me to get previous version 14 of google-chrome-stable deb package?

Thank you in advance.

starlinq

---

