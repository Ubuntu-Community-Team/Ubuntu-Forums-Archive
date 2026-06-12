---
title: "Missing packages?"
date: 2012-08-24
forum: General Help
---

### Post by shields12347 on 2012-08-24
Hey I have just installed Ubuntu from a thumb drive today and it has been acting really buggy, some programs dont open all the time and some like the software center never open. I went into the terminal and ran the command gksudo software-center and this is what I got in return.



```
2012-08-24 22:58:58,911 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-08-24 22:58:58,913 - softwarecenter.db.database - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 183, in _get_new_xapiandb
    softwarecenter.paths.APT_XAPIAN_INDEX_DB_PATH)
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3666, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2012-08-24 22:58:59,331 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-08-24 22:58:59,553 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-08-24 22:58:59,556 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/update-software-center-agent", line 73, in <module>
    cache = apt.Cache(memonly=True)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Read error - read (5: Input/output error), E:Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Read error - read (5: Input/output error), E:Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
2012-08-24 23:00:00,811 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 1
2012-08-24 23:00:00,881 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2012-08-24 23:00:01,347 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2012-08-24 23:00:01,506 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2012-08-24 23:00:01,571 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2012-08-24 23:00:01,640 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2012-08-24 23:00:01,765 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 272, in _build_homepage_view
    self._append_top_rated()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 424, in _append_top_rated
    top_rated_cat = self._update_top_rated_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 411, in _update_top_rated_content
    docs = top_rated_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/share/software-center/update-software-center-channels", line 67, in <module>
    res = check_for_channel_updates_and_trigger_axi()
  File "/usr/share/software-center/update-software-center-channels", line 53, in check_for_channel_updates_and_trigger_axi
    db._aptcache.open()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Read error - read (5: Input/output error), E:Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
```

---

### Post by 2F4U on 2012-08-25
Seems as if quite some people are having similar problems:

[http://ubuntuforums.org/showthread.php?t=1750755](http://ubuntuforums.org/showthread.php?t=1750755)

The solution mentioned in post #7 seems to fix the problem for most people.

---

### Post by shields12347 on 2012-08-25
> **2F4U said:**
> Seems as if quite some people are having similar problems:

[http://ubuntuforums.org/showthread.php?t=1750755](http://ubuntuforums.org/showthread.php?t=1750755)

The solution mentioned in post #7 seems to fix the problem for most people.

Thanks a lot! That solved it!

---

### Post by mzaam on 2012-08-25
please mark solved thread as solved

---

