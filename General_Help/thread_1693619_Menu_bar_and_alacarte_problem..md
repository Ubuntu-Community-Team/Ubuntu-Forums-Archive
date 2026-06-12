---
title: "Menu bar and alacarte problem."
date: 2011-02-23
forum: General Help
---

### Post by ValentinV on 2011-02-23
Hello i have a problem with the Menu Bar it`s not displaying the applications categories or the applications , and when i want to edit the menus with alacarte it fails to launch and i get this :
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 48, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
.

Could anyone help me ?
Thank you

---

### Post by seawolf167 on 2011-02-23
I'd try reinstalling alacarte and starting with a fresh applications menu and see if that fixes it:

Backup & remove the current applications.menu

```
cp ~/.config/menus/applications.menu ~/applications.menu.backup
rm ~/.config/menus/applications.menu
```Remove alacarte and its config files, then reinstall

```
sudo apt-get purge alacarte
sudp apt-get install alacarte
```Then run alacarte and it will auto regen the application.menu file

---

### Post by ValentinV on 2011-02-23
Thanks Sea wolf .
That solved the problem :D

---

