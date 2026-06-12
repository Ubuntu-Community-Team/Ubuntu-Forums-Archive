---
title: "Software Center and Update Manager not working after adding repository"
date: 2011-04-08
forum: General Help
---

### Post by xedi on 2011-04-08
I tried to install emergent using following guide: [http://grey.colorado.edu/emergent/index.php/Installation_(Ubuntu](http://grey.colorado.edu/emergent/index.php/Installation_(Ubuntu))

However, I did not succeed, it seems that it could not install emergent properly.

My far worse problem now is that it messed up my software center and update manager.

I get following error message when starting the software-center:

```
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 105, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 130, in open
    self._list.read_main_list()
SystemError: E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 312, in __init__
    self.view_switcher = ViewSwitcher(self.view_manager, datadir, self.db, self.cache, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 59, in __init__
    store = ViewSwitcherList(view_manager, datadir, db, cache, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 321, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 399, in _update_channel_list
    self._update_channel_list_installed_view()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 452, in _update_channel_list_installed_view
    if (pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 128, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```

My update manager is complaining, too:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'

I am too lazy to reinstall ubuntu 10.10, but I have no idea how to fix the issue, so maybe anybody here has a clue what is going on and how to fix it?

Thanks for your help in advance.

---

### Post by xedi on 2011-04-08
I also found that thread: [http://ubuntuforums.org/showthread.php?t=775038](http://ubuntuforums.org/showthread.php?t=775038)

However, I do not have those lines in my source list: 

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

deb [http://grey.colorado.edu/ubuntu](http://grey.colorado.edu/ubuntu) maverick main
deb [http://grey.colorado.edu/ubuntu](http://grey.colorado.edu/ubuntu) $(grep CODENAME /etc/lsb-release | cut -f2 -d=) main
deb-src [http://grey.colorado.edu/ubuntu](http://grey.colorado.edu/ubuntu) $(grep CODENAME /etc/lsb-release | cut -f2 -d=) main
deb [http://grey.colorado.edu/ubuntu](http://grey.colorado.edu/ubuntu) $(grep CODENAME /etc/lsb-release | cut -f2 -d=) main
deb-src [http://grey.colorado.edu/ubuntu](http://grey.colorado.edu/ubuntu) $(grep CODENAME /etc/lsb-release | cut -f2 -d=) main
deb [http://grey.colorado.edu/ubuntu](http://grey.colorado.edu/ubuntu) main
deb-src [http://grey.colorado.edu/ubuntu](http://grey.colorado.edu/ubuntu) main

---

### Post by xedi on 2011-04-08
Ahh, I just deleted the last lines from the new repository and now everything is working again :-D, sorry for bothering you.

---

