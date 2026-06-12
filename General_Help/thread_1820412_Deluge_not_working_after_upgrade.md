---
title: "Deluge not working after upgrade"
date: 2011-08-07
forum: General Help
---

### Post by polt on 2011-08-07
Hello all,

I've been having a problem with Deluge ever since upgrading to Natty.  The problem is, it doesn't open anymore.  I have the deluge-team ppa's set up and I tried completely uninstalling and reinstalling the program, but this did nothing.  When I try running Deluge via the terminal using "deluge-gtk", I get this error:

```

Traceback (most recent call last):
  File "/usr/local/bin/deluge", line 5, in <module>
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2675, in <module>
    parse_requirements(__requires__), Environment()
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 552, in resolve
    raise DistributionNotFound(req)
pkg_resources.DistributionNotFound: deluge==1.2.3

```

Any thoughts? :confused:

Thanks!

---

### Post by SalHelder on 2011-08-07
That used to happen occasionally back when I used that one. Well, have you purged deluge or just removed it? If you only removed it, try to install it again, and then:

apt-get purge deluge

And then re-install it, and see if it does something. Anyway you could use Transmission, at least is not has buggy as Deluge.

---

### Post by polt on 2011-08-07
Well, that was a nice idea, but sadly it did nothing.

---

### Post by polt on 2011-08-07
Actually, after the purge, it seems like there are still traces of some version of deluge on the computer.  The icon is still in the menu and it still attempts to open something.  Maybe that is the problem?

---

### Post by SalHelder on 2011-08-07
Maybe, since after the purge it really should have been gone of the system. Try to remove the hidden deluge folder in your home: open nautilus press Ctrl + H, and look for a page called .deluge (or something like that) and remove it. You can also try to remove the ppa and install the version in Ubuntu's repos.

---

### Post by polt on 2011-08-07
Well, I didn't find any hidden folders, but I did search through my filesystem and found about 10 old deluge folders ?!  So I deleted them all and reinstalled, and lo and behold, everything works!  Thanks!  But now I wonder what kinds of other old folders are all over my system...

---

