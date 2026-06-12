---
title: "Gnome screensaver and Xscreensaver"
date: 2006-06-09
forum: General Help
---

### Post by Hoffmann on 2006-06-09
I have installed Xscreensaver. Since I already had Gnome screensaver on my machine (and "it's not possible" to uninstall this one), I am assuming that all one needs to do is either use Gnome screensaver or Xscreensaver. I mean I would not have any conflict here. Am I correct?

---

### Post by mscman on 2006-06-09
It's very possible to remove gnome-screensaver.  Don't worry about it having to remove "ubuntu-desktop", as that's just a metapackage used to install everything necessary to get gnome up and running.  Once it's there, it's save to remove.

---

### Post by Hoffmann on 2006-06-09
[QUOTE=mscman]It's very possible to remove gnome-screensaver.  Don't worry about it having to remove "ubuntu-desktop", as that's just a metapackage used to install everything necessary to get gnome up and running.  Once it's there, it's save to remove.[/QUOTE]
Just in case, I won't uninstall Gnome.  :-|

---

### Post by grsing on 2006-06-09
You won't be uninstalling Gnome.  ubuntu-desktop doesn't contain anything itself, it's basically just a list of everything that you need for a default install of Gnome.  If you remove gnome-screensaver, the install won't have all the default parts anymore, but it will still work fine (I've done it on two machines now, no problems).

---

### Post by Hoffmann on 2006-06-09
[QUOTE=grsing]You won't be uninstalling Gnome.  ubuntu-desktop doesn't contain anything itself, it's basically just a list of everything that you need for a default install of Gnome.  If you remove gnome-screensaver, the install won't have all the default parts anymore, but it will still work fine (I've done it on two machines now, no problems).[/QUOTE]

So for any program that 'says' that ubuntu-desktop will be removed, one can continue (the uninstallation process), and the system will continue to run perfectly. Is that correct? I mean is that safe? I think not only me, but several people here have doubt/concern about that message that appears on synaptic when uninstalling some programs.
Read below:

[http://packages.ubuntulinux.org/dapper/base/ubuntu-desktop](http://packages.ubuntulinux.org/dapper/base/ubuntu-desktop)

and you will see that the debate will continue, since "...it is used to carry out certain upgrade transitions (such as adding new packages to the system)."

So, back to the original question: there is no problem if one has both Gnome screensaver and Xscreensaver installed. Right?

---

### Post by Hoffmann on 2006-06-10
Ok...
I think having both screensavers would cause no problem.

---

### Post by Gustav on 2006-06-10
The ubuntu-desktop package is good to have when you upgrade your system from one version to another (e.g. Breezy -> Dapper). 

But the rest of the time it doesn't do anything and can safely be removed.

---

### Post by Hoffmann on 2006-06-10
[QUOTE=Gustav]The ubuntu-desktop package is good to have when you upgrade your system from one version to another (e.g. Breezy -> Dapper). 

But the rest of the time it doesn't do anything and can safely be removed.[/QUOTE]
Since, probably,  I will upgrade from Dapper to Edgy in October, it would be better to keep ubuntu-desktop.
Until now I got no conflict in using xscreensaver.  It seems like, since I set xscreensaver to run, gnome screensaver just "sleeps".
:D

---

