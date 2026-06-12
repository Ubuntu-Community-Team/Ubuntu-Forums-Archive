---
title: "No longer downloadable"
date: 2010-07-31
forum: General Help
---

### Post by den_ on 2010-07-31
Hi!

I noticed that  'ubuntu-support-status --show-unsupported' reports 9 packages that are no longer downloadable.

> ubuntu-support-status --show-unsupported
Support status summary of 'denis-desktop':

You have 837 packages (47.0%) supported until April 2013 (3y)
You have 33 packages (1.9%) supported until October 2011 (18m)
You have 607 packages (34.1%) supported until April 2015 (5y)

You have 9 packages (0.5%) that can not/no-longer be downloaded
You have 294 packages (16.5%) that are unsupported

No longer downloadable:
compiz compiz-core compiz-gnome compiz-plugins indicator-application 
libappindicator0 libdecoration0 python-appindicator virtualbox-3.2 


aptitude download for each of these packages returns something like:> E: No downloadable files for indicator-application version 0.0.19-0ubuntu5; perhaps it is a local or obsolete package?

Anyone has a clue what is here going on? If these packages are obsolete, shouldn't 'aptitude update && aptitude full-upgrade' resolve this, and update them with appropriate replacement packages?

---

### Post by den_ on 2010-07-31
Ok, packages are now in ppa:compiz/ppa repository.

---

### Post by winchendonsprings on 2010-09-06
How did you fix the indicator-application problem?

---

### Post by den_ on 2010-09-06
What problem do you have with it? 

I have just added ppa:compiz/ppa repository and that was it. Btw. I am also using proposed and backports repos.

---

