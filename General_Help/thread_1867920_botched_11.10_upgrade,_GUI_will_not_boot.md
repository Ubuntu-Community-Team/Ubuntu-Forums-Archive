---
title: "botched 11.10 upgrade, GUI will not boot"
date: 2011-10-23
forum: General Help
---

### Post by moogly_google on 2011-10-23
Recently upgraded to 11.10, and in the middle of installation all processes froze up, and the comp had to be rebooted. i have no idea what package/process it was working on at the time.
restarted, and ubuntu would not boot at all. did DPKG from root and attempted to repair/upgrade packages, but numerous packages would not download/repair.
retried same thing in recovery+networking, and some more packages were repaired, but not all of them roughly 73 have yet to be repaired, and will not upgrade or download, even with --force options.
as of right now ubuntu will display the initial loading splash screen and proceed to run checks and whatnot, but it will freeze up after "checking battery state" or after initializing the music daemon, alternating. 
I have attempted to restore previous versions and repair the upgrade/packages as far as I can take it. as of right now I can login and run most programs successfully through Root, but the GUI will still not boot up, and DPKG will still not repair/upgrade the last 73 packages.

---

### Post by moogly_google on 2011-10-23
Oh, I forgot to add, I'm running a dual boot with windows 7, if that makes a difference.

---

### Post by linuxinstalledfromhdd on 2011-10-23
> **moogly_google said:**
> Oh, I forgot to add, I'm running a dual boot with windows 7, if that makes a difference.

This is why I don't use the dist-upgrade..  It is always better to do a fresh install. 

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by afz12 on 2011-10-23
I agree with that! I upgraded from 11.04 to 11.10 and it took ages, after which the screen resolution was locked into a low mode. Also, many software packages were lost. I expected this would happen so I had saved the data I wanted previously anyway. I then installed from a CD and the fresh installed worked fine. The moral is, I guess, never believe rhetoric when it comes to software behavior and implement backup measures! Most, if not all software has bugs - probably not surprisingly given the extensive scope of functionality usually incorporated.

---

### Post by moogly_google on 2011-10-23
While this is fantastic to talk about, it isn't actually helping me any.

---

### Post by linuxinstalledfromhdd on 2011-10-23
> **moogly_google said:**
> While this is fantastic to talk about, it isn't actually helping me any.

Well if nobody can help you here, your only other alternative is to reinstall your system. 

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Like I said, it is better to do a fresh install instead of using a dist-upgrade and that is why I posted the link for you to reinstall.

---

