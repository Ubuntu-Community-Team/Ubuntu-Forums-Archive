---
title: "Ubuntu Tweak 0.5.5.1 crahses on startup in kubuntu 10.04"
date: 2010-07-30
forum: General Help
---

### Post by Holy Knight on 2010-07-30
Hello everyone,I am here to share with you a rather strange problem with ubuntu tweak.I searched everywhere for the solution but could not find any.

The program crashes immediately after displaying the splash screen with the following error:

File "/usr/bin/ubuntu-tweak", line 109, in <module>
    from ubuntutweak.mainwindow import MainWindow
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py", line 148, in <module>
    MLOADER = ModuleLoader(modules.__path__[0])
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/__init__.py", line 27, in __init__
    package = __import__('.'.join([__name__, module]), fromlist=['modules'])
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/cleaner.py", line 39, in <module>
    from ubuntutweak.widgets.utils import ProcessDialog, SmartTerminal, TerminalDialog
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/widgets/utils.py", line 20, in <module>
    import vte
ImportError: No module named vte

Thats all from the error window.I await your assistance.
Thank You :)

---

### Post by dino99 on 2010-07-30
try to remove/purge then reinstall Tweak

are you using a custom package from a ppa or direct install from sources ?

---

### Post by Holy Knight on 2010-07-31
> **dino99 said:**
> try to remove/purge then reinstall Tweak

are you using a custom package from a ppa or direct install from sources ?

I went to the extent of reinstalling kubuntu,even then I received the error.I downloaded the .deb installer directly from their website.

[www.ubuntu-tweak.com](www.ubuntu-tweak.com)

All I did was to click the big download button and I got the installer.

---

### Post by RahulBatra on 2010-08-14
This solved the problem for me (on Kubuntu 10.04):

```
sudo apt-get install python-vte
```

---

