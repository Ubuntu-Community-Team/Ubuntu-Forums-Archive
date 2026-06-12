---
title: "Software Center doesn't start"
date: 2012-02-04
forum: General Help
---

### Post by rudihawk on 2012-02-04
I'm having a problem where my Ubuntu Software Center doesn't start. 

I'm using gnome-shell at the moment. 

```

rudolph@RudolphDesktop:~$ software-center
2012-02-04 14:30:01,641 - softwarecenter.ui.gtk3.em - INFO - EM's: 16 14 19
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 212, in __init__
    self.cache = get_pkg_info()
  File "/usr/share/software-center/softwarecenter/db/pkginfo.py", line 179, in get_pkg_info
    pkginfo = AptCache()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 112, in __init__
    self.apt_finished_stamp=Gio.File.new_for_path(self.APT_FINISHED_STAMP)
AttributeError: type object 'File' has no attribute 'new_for_path'

```

Does anyone have an idea as to how I can fix this problem?

---

### Post by MG&amp;TL on 2012-02-04
No. That's a bug if ever I saw one. I suggest reporting a bug on launchpad.

Sorry I can't be of more help, hope you do get it fixed, but please report it to LP.

---

### Post by rudihawk on 2012-02-04
> **MG&TL said:**
> No. That's a bug if ever I saw one. I suggest reporting a bug on launchpad.

Sorry I can't be of more help, hope you do get it fixed, but please report it to LP.

Thanks anyway :) 

I'll report it to LP.

EDIT:Updated my system and it's working again.

---

