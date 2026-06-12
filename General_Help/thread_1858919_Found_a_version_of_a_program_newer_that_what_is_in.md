---
title: "Found a version of a program newer that what is in the repository"
date: 2011-10-13
forum: General Help
---

### Post by artium on 2011-10-13
I found that one of the programs I use is outdated and that there is a newer version available at the developer's web site.

Is there something I can do in such situation?
Should I un-install the one from the repository, and install the latest version manually? This will prevent me from getting automatic updates when they get out.

---

### Post by thatguruguy on 2011-10-13
It's not unusual for the programs in the repositories to lag behind the newest releases from the developers.  The packages have to be tested and compiled for each version of Ubuntu to make their way into the repositories, and that takes time and manpower.

There are ways to address that issue, however.  Many developers (and sometimes, other users) will maintain a "personal package archives" (a "ppa") which will contain recent builds of their programs.  For instance, if you do a google search on "Ubuntu ppa firefox", you will find that there is a listing for the "Official PPA for Firefox and Thunderbird Daily Builds" available at [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa"). If you go to the page on Launchpad for the particular ppa you want, you can find instructions as to how to install the ppa to your software sources list.

Since you decided not to mention what particular program you want updated, I can't help you find out if there's a ppa for it or not.  But a quick search on google (or the search engine of your choice) may point you in the right direction.

---

### Post by haqking on 2011-10-13
> **artium said:**
> I found that one of the programs I use is outdated and that there is a newer version available at the developer's web site.

Is there something I can do in such situation?
Should I un-install the one from the repository, and install the latest version manually? This will prevent me from getting automatic updates when they get out.

just because there is a newer version doesnt mean you need it or will be stable.

If what you have works then stick with it.

The repos dont carry the latest and greatest.

Upgrading is a choice.

If you want the latest due to a new feature or whatever then just get it from the dev website as mentioned, if you want updates then look for a PPA

---

### Post by CatKiller on 2011-10-13
This is normal. Ubuntu packages don't get upgraded. Each release will include the versions of software current at the time the release was put together ("feature freeze"). These are then polished during testing for the release. Post-release packages only get security updates.

There are a handful of exceptions. Since Firefox ties its security updates to its feature updates, users generally get the latest version of Firefox, which is OK since Firefox is such a high profile application. There's a backports repository that contains software from a newer release that's been specifically tested to make sure it works in the older release. LTS releases will often get point releases through their lifetime that may include newer versions of software.

As mentioned above, using a PPA is a painless method of using newer versions of software than were included with a release.

---

### Post by stoneguy on 2011-10-13
Sometimes the newer app version uses a version of something that isn't being upgraded for stability. I've seen this with Python apps. Dev using some new feature that isn't in the language or library shipping with the release you're using, so recompiling won't work.

Stability vs uncertainty - there's a price either way.

---

