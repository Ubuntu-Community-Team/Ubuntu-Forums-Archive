---
title: "Gnome-App-Install problem"
date: 2010-01-20
forum: General Help
---

### Post by Burky on 2010-01-20
I get this error message when trying to start Gnome-App-Install (aka Add/Remove prior Karmic). I'm using 32-bit Karmic Koala. 

```
david@david-desktop:~$ /usr/bin/gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/share/gnome-app-install/AppInstall/activation.py", line 483, in main
    from AppInstall.AppInstallApp import AppInstallApp
  File "/usr/share/gnome-app-install/AppInstall/AppInstallApp.py", line 51, in <module>
    import distros
  File "/usr/share/gnome-app-install/AppInstall/distros/__init__.py", line 4, in <module>
    from Default import Distribution as _default
  File "/usr/share/gnome-app-install/AppInstall/distros/Default.py", line 1, in <module>
    from AppInstall.Menu import SHOW_ALL, SHOW_ONLY_SUPPORTED, SHOW_ONLY_FREE, SHOW_ONLY_MAIN, SHOW_ONLY_PROPRIETARY, SHOW_ONLY_THIRD_PARTY, SHOW_ONLY_INSTALLED
  File "/usr/share/gnome-app-install/AppInstall/Menu.py", line 16, in <module>
    import gst
ImportError: No module named gst

```

---

