---
title: "ubuntu tweak won't open"
date: 2012-09-09
forum: General Help
---

### Post by snowlizard31 on 2012-09-09
I've installed ubuntu tweak but It won't open from the terminal or from dash
```

snowlizard@snowlizard-iMac:~/Desktop$ ubuntu-tweak
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 124, in <module>
    from ubuntutweak.main import UbuntuTweakWindow
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 40, in <module>
    from ubuntutweak.preferences import PreferencesDialog
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/preferences.py", line 32, in <module>
    from ubuntutweak.factory import WidgetFactory
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/factory.py", line 24, in <module>
    from ubuntutweak.gui.widgets import *
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/gui/widgets.py", line 10, in <module>
    from ubuntutweak.settings.compizsettings import CompizSetting
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/compizsettings.py", line 4, in <module>
    import compizconfig
ImportError: /usr/lib/python2.7/dist-packages/compizconfig.so: undefined symbol: ccsDefaultInterfaceTable

```

---

