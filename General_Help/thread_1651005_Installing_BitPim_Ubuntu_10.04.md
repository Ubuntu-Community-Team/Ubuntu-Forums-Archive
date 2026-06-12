---
title: "Installing BitPim Ubuntu 10.04"
date: 2010-12-22
forum: General Help
---

### Post by ksaul on 2010-12-22
I followed [http://ubuntuforums.org/showthread.php?t=145946](http://ubuntuforums.org/showthread.php?t=145946) that thread for installing BitPim on 10.04, but am getting this error:

> 
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.3/initscripts/ConsoleSetLibPath.py", line 35, in <module>
  File "src/bp.py", line 20, in <module>
  File "src/bp_cli.py", line 21, in <module>
  File "src/bp_config.py", line 19, in <module>
  File "src/guihelper.py", line 23, in <module>
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
  File "ExtensionLoader_wx__core_.py", line 12, in <module>
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory


what do i dooooo? lol
help please :)

---

### Post by ksaul on 2010-12-22
Nevermind, I ended up installing it right from the software manager and works great

---

