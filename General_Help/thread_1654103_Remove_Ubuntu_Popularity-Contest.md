---
title: "Remove Ubuntu Popularity-Contest"
date: 2010-12-27
forum: General Help
---

### Post by AggravatedGestalt on 2010-12-27
I see that this subject has been discussed in other releases, but not yet for Lucid Lynx LTS. I would like to remove popularity-contest, though it seems it wants to take ubuntu-standard with it. I uninstalled evolution-database once to have gnome completely removed and my system pretty much toasted. I've had similar issues with purging network-manager (wicd rocks!) too. It seems that many things are becoming embedded into ubuntu similar to old microsoft, and cannot be removed. My volume-icon is removed by removing evolution from the panel! I like to maintain a clean system by my own standards, and do not understand why things have been designed this way. I know it is convenient to bind certain programs like evolution, but why can I not remove popularity-contest? If I can remove this feature, please tell me how.

---

### Post by dcstar on 2010-12-28
> **AggravatedGestalt said:**
> I see that this subject has been discussed in other releases, but not yet for Lucid Lynx LTS. I would like to remove popularity-contest, though it seems it wants to take ubuntu-standard with it. I uninstalled evolution-database once to have gnome completely removed and my system pretty much toasted. I've had similar issues with purging network-manager (wicd rocks!) too. It seems that many things are becoming embedded into ubuntu similar to old microsoft, and cannot be removed. My volume-icon is removed by removing evolution from the panel! I like to maintain a clean system by my own standards, and do not understand why things have been designed this way. I know it is convenient to bind certain programs like evolution, but why can I not remove popularity-contest? If I can remove this feature, please tell me how.

There is little to gain by removing this trivial package. It will not do anything if this file has PARTICIPATE="no": /etc/popularity-contest.conf

Don't waste your time with this, it is part of all Debian based distros.

---

### Post by XeonBloomfield on 2010-12-28
System > Administration > Software Sources.

In tab "Statistics" uncheck "Submit statistical information".

Disabling it in any other way (except direct config modifing like said last poster) is waste of your time.

---

### Post by holiday on 2010-12-30
I made /etc/cron.daily/popularity-contest non-executable. 

$ sudo chmod -x  /etc/cron.daily/popularity-contest.

I don't know that it's going to work. If it does, it might be for just a little while. The installers have root access. I remember disabling this once before through some other method. I don't really know what popularity-contest does but I see in the script that it sends an email from my machine. I don't remember saying that was ok. Explicitly, I mean. 

The /etc/cron.* directories are an interesting browse. 

I'm not crying "Evil", but I am crying "Foul". I might consent to sending information if I am given the opportunity, and could view the information I've sent and also, of course, the distribution list. I might find that interesting enough to participate.

---

### Post by ibuclaw on 2010-12-30
Very little information does get submitted.

[http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

As a packager, it gives me an idea of how many people use the software I develop.

---

### Post by chrisstankevitz on 2011-07-17
> **XeonBloomfield said:**
> System > Administration > Software Sources.

In tab "Statistics" uncheck "Submit statistical information".

Disabling it in any other way (except direct config modifing like said last poster) is waste of your time.

Are you saying it is a waste of time because the OS will re-enable the "popularity-contest" if we try to disable it?

Chris

---

