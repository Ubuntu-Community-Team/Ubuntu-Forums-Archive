---
title: "Lost access to the unity interface how to fix? (ubuntu 11.10)"
date: 2011-11-18
forum: General Help
---

### Post by talgalili on 2011-11-18
o.k, this is embarrassing:

I have installed Compiz Config Settings Manager and tried to fix it so that the transition time between changing tabs (using alt+tab) will be short.  by accident I un-pressed V from something else, and it asked me about a conflict - I pressed the "x" button to close the window and as a result I stopped seeing the unity interface.  That is - I can not see any buttons of the left side.

I went to the terminal (ctrl+alt+F1) and ran 

    ccsm

As a result I got the following error:



    $ ccsm
    /usr/lib/python2.7/site-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
      warnings.warn(str(e), _gtk.Warning)
    Traceback (most recent call last):
      File "/usr/bin/ccsm", line 93, in <module>
        import ccm
      File "/usr/lib/python2.7/site-packages/ccm/__init__.py", line 1, in <module>
        from ccm.Conflicts import *
      File "/usr/lib/python2.7/site-packages/ccm/Conflicts.py", line 26, in <module>
        from ccm.Constants import *
      File "/usr/lib/python2.7/site-packages/ccm/Constants.py", line 29, in <module>
        CurrentScreenNum = gtk.gdk.display_get_default().get_default_screen().get_number()
    AttributeError: 'NoneType' object has no attribute 'get_default_screen'


What should I do next?


Thanks.

---

### Post by talgalili on 2011-11-18
I found a solution and posted it here:

This seemed fixed once I went to terminal (ctrl+alt+F1) and pressed:

gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config

source: [http://ubuntuforums.org/showthread.php?t=1866462](http://ubuntuforums.org/showthread.php?t=1866462)

---

