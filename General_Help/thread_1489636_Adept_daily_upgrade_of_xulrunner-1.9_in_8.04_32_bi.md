---
title: "Adept daily upgrade of xulrunner-1.9 in 8.04 32 bit"
date: 2010-05-21
forum: General Help
---

### Post by hangfire on 2010-05-21
I am running firefox-mozilla-build (3.6.3-0ubuntu1) on 8.04 32 bit (this is not the system listed in my sig or user information). In general it works very, very well.

Every day Adept has me update xulrunner-1.9.

I can run apt-get autoremove, update, upgrade with no errors.

I see others on this forum have this error, but I can find no solutions posted for it.

I used to run Namoroka 3.6.2pre from launchpad and had the same problem. Nothing could uninstall it except Synaptic "Completely remove". I removed all firefoxes and xulrunner at that time and then reinstalled 3.6.3 which works great. I hoped that would fix the xulrunner issue but no dice.

While running 3.6.2pre I had the same issue.

-HF

---

### Post by hangfire on 2010-05-22
Bump.

---

### Post by hangfire on 2010-05-28
It came back the next day.

I did a (from memory, might not be exactly correct):

 **[FONT="Courier New"]dpkg --purge xulrunner xurunner-1.9[/FONT]** 

and it is gone and has stayed gone.

I post this for anyone else trying to wean their 8.04/9.04/9.10 off of a beta Firefox. Uninstall is not a strength with these packages.

-HF

---

