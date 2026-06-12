---
title: "Synce problem"
date: 2010-05-09
forum: General Help
---

### Post by rules on 2010-05-09
Hi

I have been successfully using Synce to sync my phone (HTC TD2) with my laptop. It would seem though, after the last update, that it has stopped working. 

Here is what it shows me ... 

rafiq@rafiq-laptop:~$ synce-kpm
The dataserver is already running....
rafiq@rafiq-laptop:~$ Traceback (most recent call last):
  File "/usr/bin/synce-kpm", line 26, in <module>
    synceKPM.main.main()
  File "/usr/lib/python2.6/dist-packages/synceKPM/main.py", line 74, in main
    import synceKPM.main_gui
  File "/usr/lib/python2.6/dist-packages/synceKPM/main_gui.py", line 6, in <module>
    from synceKPM.gui.mainwindow import *
  File "/usr/lib/python2.6/dist-packages/synceKPM/gui/mainwindow.py", line 30, in <module>
    from synceKPM.gui.ui_synce_kpm_mainwindow import *
  File "/usr/lib/python2.6/dist-packages/synceKPM/gui/ui_synce_kpm_mainwindow.py", line 7, in <module>
    from PyKDE4 import kdecore
ImportError: No module named PyKDE4
rafiq@rafiq-laptop:~$ 


I have tried reinstalling but it still doesn't want to start.

Any ideas?

Cheers.

---

### Post by rules on 2010-05-11
Just figured it out ... searched Synaptic for "PyKDE4", installed it and bingo ... Now it even shows you a picture of the phone connected :)

---

