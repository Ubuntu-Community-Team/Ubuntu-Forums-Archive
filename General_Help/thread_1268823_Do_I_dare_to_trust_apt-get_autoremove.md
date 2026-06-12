---
title: "Do I dare to trust apt-get autoremove?"
date: 2009-09-17
forum: General Help
---

### Post by PatrikG on 2009-09-17
I did a clean-up a couple of days ago with the "Computer Janitor" app and (stupidly enough) just clicked OK to whatever it wanted to remove. But then after doing a refresh it wanted to remove a whole bunch of stuff, and I've seen somewhere that the computer janitor is not that trustworthy.

Anyway, I did a sudo apt-get autoremove, and I got the following rather big list:

The following packages were automatically installed and are no longer required:
  debhelper intltool-debian postfix libbeecrypt6 lsb-graphics lsb-desktop m4 po-debconf ncurses-term libmail-sendmail-perl gettext librpm4.4 libqt4-gui lsb pax rpm bsd-mailx html2text libqt3-mt mailx lsb-core alien libsys-hostname-long-perl lsb-cxx

The following packages will be REMOVED:
  alien bsd-mailx debhelper gettext html2text intltool-debian libbeecrypt6 libmail-sendmail-perl libqt3-mt libqt4-gui librpm4.4
  libsys-hostname-long-perl lsb lsb-core lsb-cxx lsb-desktop lsb-graphics m4 mailx ncurses-term pax po-debconf postfix rpm

Can I really trust this result? To me it seems like a lot of packages...

---

### Post by SuperSonic4 on 2009-09-17
Looks fine to me but then I don't know/care what you run

---

### Post by NightwishFan on 2009-09-17
I think it is fine. None of those packages seem dire essential. If you are worried just leave them installed. If you break anything just install the package ubuntu-desktop to get the whole of Ubuntu back.

---

### Post by Don1500 on 2009-09-17
> **SuperSonic4 said:**
> Looks fine to me but then I don't know/care what you run

Good answer, may I use it as my sig?

---

### Post by shylent on 2009-09-17
Yeah, I agree, those packages are fine to remove. But really, this goes to show just how bad apt-get is at anything besides installing stuff. With aptitude you would've never had to deal with this mess - using aptitude, when you remove a package, it auto-removes all of its dependencies (only if those were auto-installed and have no more packages depending on them, so you never break stuff). Janitor. Ha!

---

### Post by NightwishFan on 2009-09-17
Well, apt-get just waits for you to manually wipe them I guess. It is a backend tool, whereas aptitude is a frontend.

---

### Post by SuperSonic4 on 2009-09-17
> **Don1500 said:**
> Good answer, may I use it as my sig?

Go ahead :)

---

