---
title: "calibre causes gnome to restart"
date: 2011-02-08
forum: General Help
---

### Post by dakers001 on 2011-02-08
Recently I tried to install calibre ebook management software from the Ubuntu Software center and it installed fine as expected, ran fine from the applications menu as expected (for the initial run) went through the wizard and clicked next.  All of a sudden I was presented with a login prompt.  I thought I must have hit a hot key accidentally, so I logged in and it restarted fresh not like the desktop was locked.  So I ran calibre again and it did the same thing. I uninstalled calibre and went about compiling from source, after all of the dependencies were met and it compiled and installed ran it again and it logged me out again.  Does anyone have a clue what I should try to resolve this.

System:
Ubuntu 10.10
Kernel 2.6.35-25-generic
Gnome 2.32.0
Memory 1GB
Pentium 4 2.6ghz

---

### Post by cmallam on 2011-02-16
doesn't work for me either

calibre
Traceback (most recent call last):
  File "/usr/bin/calibre", line 19, in <module>
    sys.exit(main())
  File "/usr/lib/calibre/calibre/gui2/main.py", line 321, in main
    app, opts, args, actions = init_qt(args)
  File "/usr/lib/calibre/calibre/gui2/main.py", line 40, in init_qt
    from calibre.gui2.ui import Main
  File "/usr/lib/calibre/calibre/gui2/ui.py", line 31, in <module>
    from calibre.gui2.widgets import ProgressIndicator
  File "/usr/lib/calibre/calibre/gui2/widgets.py", line 26, in <module>
    from calibre.gui2.progress_indicator import ProgressIndicator as _ProgressIndicator
  File "/usr/lib/calibre/calibre/gui2/progress_indicator/__init__.py", line 15, in <module>
    pi_error)
RuntimeError: Failed to load the Progress Indicator plugin: the sip module implements API v8.0 but the progress_indicator module requires API v7.1

---

