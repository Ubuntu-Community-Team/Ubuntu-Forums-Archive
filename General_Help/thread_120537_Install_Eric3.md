---
title: "Install Eric3?"
date: 2006-01-22
forum: General Help
---

### Post by not_yet on 2006-01-22
I have a fresh install of Breezy

I would like to use Eric3, a python ide

Eric3 is available from Synaptic

After install I get a seg fault when I try to run it?:???: 

Any suggestions:) 

Errors as follows:

-->notyet@ubuntu:/usr/bin$ ./eric3
Traceback (most recent call last):
  File "/usr/lib/site-python/eric3/eric3.py", line 147, in ?
    main()
  File "/usr/lib/site-python/eric3/eric3.py", line 132, in main
    mw = UserInterface(loc, splash)
  File "/usr/lib/site-python/eric3/UI/UserInterface.py", line 265, in __init__
    self.sbv = SBVviewer(dbs, self.sbvDock, 1)
  File "/usr/lib/site-python/eric3/UI/SBVviewer.py", line 75, in __init__
    self.stackComboBox.sizePolicy().hasHeightForWidth()))
TypeError: argument 1 of QSizePolicy() has an invalid type
Segmentation fault

---

### Post by not_yet on 2006-01-25
bump - ee :) 

anyone manage to get eric3 to work?

---

### Post by mcmuffy on 2006-01-25
I have the newest version installed and it works fine. Have you checked the dependency list to be sure you have everything required?

---

### Post by not_yet on 2006-01-25
I'm glad someone has it working:) \

question: did you install via synaptic??

where do I find the dependancy list??

thx

---

### Post by mcmuffy on 2006-01-26
I downloaded and installed from source found at [http://www.die-offenbachs.de/detlev/eric3.html](http://www.die-offenbachs.de/detlev/eric3.html). If memory serves the dependancies are listed in a readme within the archive.

---

