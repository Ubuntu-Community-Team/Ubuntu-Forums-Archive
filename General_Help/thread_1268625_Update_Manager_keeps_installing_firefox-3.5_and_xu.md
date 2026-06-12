---
title: "Update Manager keeps installing firefox-3.5 and xulrunner-1.9.1 (almost daily)"
date: 2009-09-17
forum: General Help
---

### Post by petru.marginean on 2009-09-17
Hi,

Almost every day I download and install a few firefox related packages.
For example these are the packages installed today:

> Upgraded the following packages:
firefox (3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~jaunty) to 3.5.4~hg20090916r26379+nobinonly-0ubuntu1~umd1~jaunty
firefox-3.5 (3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~jaunty) to 3.5.4~hg20090916r26379+nobinonly-0ubuntu1~umd1~jaunty
firefox-3.5-branding (3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~jaunty) to 3.5.4~hg20090916r26379+nobinonly-0ubuntu1~umd1~jaunty
xulrunner-1.9.1 (1.9.1.4~hg20090914r26358+nobinonly-0ubuntu2~umd1~jaunty) to 1.9.1.4~hg20090916r26379+nobinonly-0ubuntu2~umd1~jaunty
or yesterday:

> Upgraded the following packages:
firefox (3.5.4~hg20090914r26356+nobinonly-0ubuntu1~umd1~jaunty) to 3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~jaunty
firefox-3.5 (3.5.4~hg20090914r26356+nobinonly-0ubuntu1~umd1~jaunty) to 3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~jaunty
firefox-3.5-branding (3.5.4~hg20090914r26356+nobinonly-0ubuntu1~umd1~jaunty) to 3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~jaunty
xulrunner-1.9.1 (1.9.1.4~hg20090914r26356+nobinonly-0ubuntu1~umd1~jaunty) to 1.9.1.4~hg20090914r26358+nobinonly-0ubuntu2~umd1~jaunty
Is this normal?

Regards,
Petru

---

### Post by petru.marginean on 2009-09-20
It keeps happening, every day.

The same 4 x packages get upgraded every day: 
- firefox
- firefox-3.5
- firefox-3.5-branding
- xulrunner-1.9.1

Any idea why?

Regards,
Petru

---

### Post by drs305 on 2009-09-20
Did you happen to use the Firefox daily build repositories to download your versions of Firefox? As the name implies, the nightly builds will be updated very often.  ;-)

If not, did your change your repositories in any other way to gain access to the newer versions?

And of course, you could reduce the frequency of all updates by setting a longer interval. In Synaptic, you can do it via Settings, Repositories, Updates.

---

### Post by slakkie on 2009-09-20
Looks to be daily builds indeed. Otherwise you could pin the package to the current version you have right now..

---

### Post by petru.marginean on 2009-09-20
Hi,

I've checked and found this in "Third party sofware" sources:

http://[ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu")

Many thanks for help!

Regards,
Petru

---

### Post by petru.marginean on 2012-07-17
Closing this issue.

---

