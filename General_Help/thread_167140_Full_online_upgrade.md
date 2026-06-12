---
title: "Full online upgrade?"
date: 2006-04-27
forum: General Help
---

### Post by SteinbergerNate on 2006-04-27
I was just looking to switch distros and I was wondering if there is a way to do a full upgrade from one version of Ubuntu to another over the internet. (say I install 5.10 today and in a couple months want 6.06 but don't want to download and burn another iso or order the new cd.)

---

### Post by az on 2006-04-27
[QUOTE=SteinbergerNate]I was just looking to switch distros and I was wondering if there is a way to do a full upgrade from one version of Ubuntu to another over the internet. (say I install 5.10 today and in a couple months want 6.06 but don't want to download and burn another iso or order the new cd.)[/QUOTE]
Running breezy, when Dapper is released, the notifier will tell you that you can upgrade to it.  Just click on it and it wil do the work for you.

By hand, you would just change the sources for apt and update, then dist-upgrade.  You can do this using synpatic.

The "under-the-hood" work is:

"breezy" is changed to "dapper" on each line in /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by elamericano on 2006-04-27
Is the result identical to a new installation of Dapper? If read discussions where people think they have issues because of having a Dapper upgrade, rather than a true Dapper install. Is this a real concern?

---

### Post by aysiu on 2006-04-27
[QUOTE=elamericano]Is the result identical to a new installation of Dapper?[/QUOTE] Yes, except you'll have extra programs installed (the ones that didn't just come with Breezy that you installed yourself.

Full upgrade instructions here:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by az on 2006-04-28
[QUOTE=elamericano] If read discussions where people think they have issues because of having a Dapper upgrade, rather than a true Dapper install. Is this a real concern?[/QUOTE]

Well, Dapper is still beta, so there may be loose ends.  If you have installed some software without using the package manager or by using foreign repositores, you may get into trouble...

99.9 percent of the time, it is fixable.  It just may be more convenient for some people to reinstall , rather than looking for the way to fix it.

This is where the forum may save you some time.

---

