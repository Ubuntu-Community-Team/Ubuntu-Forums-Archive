---
title: "can't log in to KDE after upgrading to 4.6"
date: 2011-01-26
forum: General Help
---

### Post by dlenmn on 2011-01-26
I just upgraded my Kubuntu 10.10 installation to [KDE 4.6]("http://www.kubuntu.org/news/kde-sc-4.6"), and now I can't log in to KDE. I restarted after the install was finished, and I got a message stating that KDE was no longer a login option. Indeed, failsafe (and default) are now my only login options.

Any idea how to fix this? This isn't how "upgrades" should work...

---

### Post by Memento on 2011-01-26
Same problem here...

---

### Post by Odur on 2011-01-26
And here too...

---

### Post by dlenmn on 2011-01-26
Since it's not just me, I've [reported]("https://bugs.launchpad.net/ubuntu/+bug/708151") a bug.

Add your two cents on the bug report if you also have this problem.

---

### Post by DZ* on 2011-01-26
Kpackagekit offered KDE 4.6 upgrade this morning (138 packages from ppa:kubuntu-ppa/backports) but I noticed that in the process it also wanted to remove many other packages, including "ubuntu-desktop". I switched to command line (sudo aptitude update; sudo aptitude upgrade) and aptitude refused to upgrade, with this output:

Resolving dependencies...                
open: 1604; closed: 1718; defer: 109; conflict: 427                                      No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 138 not upgraded.

---

### Post by Memento on 2011-01-26
> **DZ* said:**
> Kpackagekit offered KDE 4.6 upgrade this morning (138 packages from ppa:kubuntu-ppa/backports) but I noticed that in the process it also wanted to remove many other packages, including "ubuntu-desktop". I switched to command line (sudo aptitude update; sudo aptitude upgrade) and aptitude refused to upgrade, with this output:

Resolving dependencies...                
open: 1604; closed: 1718; defer: 109; conflict: 427                                      No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 138 not upgraded.
Maybe they finished updating the packages after you tried to upgrade (about 5 hours ago)?.
Does aptitude still give you that answer?

---

### Post by DZ* on 2011-01-26
> **Memento said:**
> Maybe they finished updating the packages after you tried to upgrade (about 5 hours ago)?.
Does aptitude still give you that answer?

Yes, it still does. It's puzzling why a KDE upgrade would want to remove ubuntu-desktop which is a Gnome meta-package.

---

### Post by Memento on 2011-01-26
> **DZ* said:**
> Yes, it still does. It's puzzling why a KDE upgrade would want to remove ubuntu-desktop which is a Gnome meta-package.
Well i guess i'd better off doing a new fresh install since i have a separate home partition...
thank you anyway ;)

---

### Post by DZ* on 2011-01-26
> **Memento said:**
> Well i guess i'd better off doing a new fresh install since i have a separate home partition...
thank you anyway ;)

Are you using GDM? I wonder if you'd be able to login if you switch to KDM
(sudo dpkg-reconfigure gdm)

---

### Post by Memento on 2011-01-26
> **DZ* said:**
> Are you using GDM? I wonder if you'd be able to login if you switch to KDM
(sudo dpkg-reconfigure gdm)
I was using kdm as kubuntu was the only o.s.
but i thought i'd give it a try and installed gdm with its dependencies...
now i can login into a gnome session with gdm and kdm, still no sign of kde (as if kdm and gdm don't recognise it).

---

### Post by rkoma on 2011-01-26
I had the same issue, after upgrade to 4.6 I am not able to login. After login, there is a blank screen for a moment and greeter is presented again. It looks like X is restarted.

I have managed to login using the following:

1. open console with Ctrl+Alt+F1 and login
2. stop kdm with *sudo service kdm stop*
3. *startx*

Login starts normally and desktop is presented.

However, normal login through greeter is still not possible. It looks like something between greeter and login process is not working; maybe it is related to the fact that there are no kdm session in the session list. Any ideas?

---

### Post by rkoma on 2011-01-26
It is solved, at least for me. The problem is in */etc/kde4/kdm/kdmrc* file. Variable *SessionsDirs* should be uncommented, and kdm should be restarted. Now in greeter it is possible to select kde from the sessions list.

*SessionsDirs* should point to directories where kdm searches for .desktop files, which defines the session to be used. Session list in greeter is populated via those .desktop files.

What is strange to me, is that the *SessionsDirs* variable is set to the same value as default (*/usr/share/xsessions,/var/lib/menu-xdg/xsessions,/usr/share/apps/kdm/sessions*), this seems like a bug to me.

---

### Post by dlenmn on 2011-01-26
Looks like things are working again after I apt-get installed kubuntu-desktop (it had been removed previously). I did an apt-get update before installing -- you might want to try the same.

---

