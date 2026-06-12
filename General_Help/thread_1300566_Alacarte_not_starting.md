---
title: "Alacarte not starting"
date: 2009-10-25
forum: General Help
---

### Post by conb123 on 2009-10-25
Hiya i recently had to remove my .gnome .gconf and .gconfd folders because gconf was giving loads of errors on startup. But now i look under applications and they have all gone. I tried to start up main menu but it fails and when i run alacarte from terminal i get this error

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
```

Any ideas?

---

### Post by dv3500ea on 2009-10-25
You probably shouldn't have done that!
Did you back up those folders? If so try restoring them from the backup location.
Are there folders of the same name in /etc/skel?  If so try restoring them from there.

---

### Post by conb123 on 2009-10-25
Oh crap well i was under the impression that they auto restored. I don't really back up so i don't have copies, and no there are no copies in /etc/skel just .bash_logout .bashrc and .profile. Also looking at the folder i removed, .gconf and .gconfd seem to have recovered but .gnome is empty.

---

### Post by conb123 on 2009-10-25
Ok for anyone else experiencing this same problem it was because of alacarte trying to write the applications.menu file which contains the menu configuration when my disk was full so it wrote the file with 0 bytes of data. This can be fixed by doing the following:

1. Check whether the file ~/.config/menus/applications.menu contains any data, if it does your problem is related to something else if it has nothing inside it continue to step 2

2. Run this in terminal, rm ~/.config/menus/applications.menu

3. Then finally run alacarte in terminal, this will cause alacarte to recreate the applications.menu file from system defaults and should hopefully fix your problem

---

