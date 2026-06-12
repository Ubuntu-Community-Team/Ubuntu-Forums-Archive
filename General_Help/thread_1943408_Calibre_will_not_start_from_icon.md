---
title: "Calibre will not start from icon"
date: 2012-03-19
forum: General Help
---

### Post by mkstallings1 on 2012-03-19
Calibre will not start from the icon.  When I typed "calibre" into the terminal this is what I get:


mike@mike-Pavilion-dv8000-EP409UA-ABA:~$ calibre
Traceback (most recent call last):
  File "/usr/bin/calibre", line 19, in <module>
    sys.exit(main())
  File "/usr/lib/calibre/calibre/gui2/main.py", line 372, in main
    app, opts, args, actions = init_qt(args)
  File "/usr/lib/calibre/calibre/gui2/main.py", line 51, in init_qt
    from calibre.gui2.ui import Main
  File "/usr/lib/calibre/calibre/gui2/ui.py", line 31, in <module>
    from calibre.gui2.widgets import ProgressIndicator
  File "/usr/lib/calibre/calibre/gui2/widgets.py", line 27, in <module>
    history = XMLConfig('history')
  File "/usr/lib/calibre/calibre/utils/config.py", line 241, in __init__
    self.refresh()
  File "/usr/lib/calibre/calibre/utils/config.py", line 252, in refresh
    with ExclusiveFile(self.file_path) as f:
  File "/usr/lib/calibre/calibre/utils/lock.py", line 113, in __enter__
    self.file  =  WindowsExclFile(self.path, self.timeout) if iswindows else open(self.path, 'a+b')
IOError: [Errno 13] Permission denied: '/home/mike/.config/calibre/history.plist'

Any ideas?

---

