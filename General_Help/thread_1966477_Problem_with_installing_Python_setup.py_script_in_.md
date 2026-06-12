---
title: "Problem with installing Python setup.py script in 12.04"
date: 2012-04-27
forum: General Help
---

### Post by rpk94 on 2012-04-27
I go to the directory the .py file is stored, and I get the following errors.
```
roopak@roopak-945GCMX-S2:~/Downloads/syspeek-0.2$ python setup.py install
running install
running build
running build_py
running build_i18n
intltool-update -p -g syspeek
running build_icons
running build_help
running install_lib
running install_data
running install_egg_info
Removing /usr/local/lib/python2.7/dist-packages/syspeek-0.2.egg-info
error: /usr/local/lib/python2.7/dist-packages/syspeek-0.2.egg-info: Permission denied

```
How can i gain the required permissions?

---

### Post by imachavel on 2012-04-27
well try sudo su&#8230; errr, CORRECTED: sudo -i
 
:guitar:
 
it's possible the upgrade messed up your python. Can you:
 
sudo apt-remove python?
 
Don't remember if that's the exact command. Remove it, then in software sources search for it and install it again
 
My upgrade majorly failed, going to go through some terminal steps in here:
 
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)
 
and copy and paste the syntax return from each command in a new thread. Don't know if it will help you out though

---

### Post by rpk94 on 2012-04-27
I did not upgrade. I wiped my system and made a fresh install a few hours ago. So the python is a new install. the sudo -i did not work. It had worked in 11.10.

---

