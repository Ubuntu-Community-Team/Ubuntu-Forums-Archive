---
title: "Main Menu under System Preferences not opening"
date: 2009-12-31
forum: General Help
---

### Post by mbslrm on 2009-12-31
I tried typing alacarte in Terminal, but I get this. =/

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 44, in __loadMenus
    self.applications.path = os.path.join(util.getUserMenuPath(), self.applications.tree.get_menu_file())
  File "/usr/lib/pymodules/python2.6/Alacarte/util.py", line 135, in getUserMenuPath
    os.makedirs(menu_dir)
  File "/usr/lib/python2.6/os.py", line 157, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permission denied: '/home/user/.config/menus'

```

Also, I've installed a copy of firefox in my home folder and I want to add it to my panel. I wrote "/home/*name*/firefox/firefox" under command, but it won't work. I also tried putting sudo in front to no avail.

---

### Post by mbslrm on 2009-12-31
bump

---

### Post by mbslrm on 2009-12-31
Can someone please help?

---

### Post by edu65 on 2010-01-05
Hi,

I had the same problem (Ubuntu 8.04 on AMD64). For some strange reason, the folder ~/.config/menus was not owned by a normal user but was owned by root instead.

Try this:

1. Open a terminal

2. Type
        cd .config

3. Type
        sudo chown -R <username>.<username> menus

   Replace <username> with your actual user name.
   You will be asked to type your password.


Hope this helps.

Ed

---

