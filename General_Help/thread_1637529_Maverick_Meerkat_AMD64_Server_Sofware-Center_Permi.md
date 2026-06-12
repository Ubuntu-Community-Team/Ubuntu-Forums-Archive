---
title: "Maverick Meerkat AMD64 Server Sofware-Center Permissions Problem"
date: 2010-12-04
forum: General Help
---

### Post by ProgressionMurph on 2010-12-04
Hello Everyone,

I am trying to start the software center by  clicking the icon in the ubuntu dropdown menu.  When I click the icon it  shows up on my task bar but then disappears.  A side note that may be  related when I try to edit my menu's nothing opens.  Anyway..back to the  main point when I type in software-center in the terminal the following  comes back.
```

alex@soapbox:~$ software-center
2010-12-04  15:57:47,409 - softwarecenter.fixme - WARNING - logs to the root logger:  '('/usr/share/software-center/softwarecenter/db/database.py', 96,  'open')'
2010-12-04 15:57:47,409 - root - WARNING - failed to add sca db Couldn't detect type of database
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 383, in __init__
    self.config = get_config()
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 43, in get_config
    _software_center_config = SoftwareCenterConfig(SOFTWARE_CENTER_CONFIG_FILE)
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 28, in __init__
    os.makedirs(os.path.dirname(config))
  File "/usr/lib/python2.6/os.py", line 157, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permission denied: '/home/alex/.config/software-center'
alex@soapbox:~$ 
```

I  assume this is a permissions related error.  However I don't know where  to begin to diagnose the problem.  I attempted to alter the permissions  of the software-center file located in /home/alex/.config/ but to no  avail I still have the same problem.

Looking forward to the responses,
Sincerely,
Alex

---

