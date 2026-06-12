---
title: "Installation of Easygui via terminal"
date: 2012-03-06
forum: General Help
---

### Post by Hiuhu on 2012-03-06
Am trying to install a  package called Easy GUI via the terminal and this is what I get :
jemoh@Hiuhu:~$ sudo python '/home/jemoh/Downloads/easygui_version_0.96_docs/setup.py' install
[sudo] password for jemoh: 
running install
running build
running build_py
file easygui.py (for module easygui) not found
file easygui.py (for module easygui) not found
running install_lib
warning: install_lib: 'build/lib.linux-i686-2.6' does not exist -- no Python modules to install
running install_egg_info
Removing /usr/local/lib/python2.6/dist-packages/easygui-0.96.egg-info
Writing /usr/local/lib/python2.6/dist-packages/easygui-0.96.egg-info
What could be the problem bcoz its not installing

---

### Post by _0R10N on 2012-03-06
Check that this lib exists
```
build/lib.linux-i686-2.6
```
If so, you might need to change the permissions of the directory containing your program.

---

