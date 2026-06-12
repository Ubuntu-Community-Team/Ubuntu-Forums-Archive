---
title: "Ubuntu Software Center will not open"
date: 2012-09-24
forum: General Help
---

### Post by cezellen on 2012-09-24
I'm still pretty new to ubuntu, and I recently had a problem with my computer, but I managed to fix it.

Now i am faced with a bigger problem, Ubuntu software center will not open.

Here is what happens when i run it in terminal,


2012-09-24 17:10:53,376 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-09-24 17:10:53,515 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
Traceback (most recent call last):
  File "/usr/bin/software-center", line 142, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 305, in __init__
    self.backend = get_install_backend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend.py", line 88, in get_install_backend
    install_backend = AptdaemonBackend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 211, in __init__
    self._on_lowlevel_transactions_changed)
AttributeError: 'AptdaemonBackend' object has no attribute '_on_lowlevel_transactions_changed'



Whatdo?

---

### Post by Bashing-om on 2012-09-24
cezellen; Hi ! welcome to the forum.

Let us go to a lower level and see about isolating the fault.

Please post the output from the terminal command:
```
sudo apt-get update
```

The errors generated in using this command will tell me more.

[INDENT]regards ==>BDQ

[/INDENT]

---

