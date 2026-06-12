---
title: "Help With Applications not working."
date: 2010-02-07
forum: General Help
---

### Post by Nick43092 on 2010-02-07
I just logged in to my laptop, and suddenly, the Applications menu doesn't work. I click on it, and there is only a little 20 pixel wide box. The Places and System menus still drop down as normal. I cannot use the edit menus option either... 

I'm running 9.04, i686, and I would appreciate any ideas anyone has, thanks!

---

### Post by Nick43092 on 2010-02-07
Maybe this output will help someone - obviously from terminal:

nick@ubuntu:~$ sudo alacarte
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

---

### Post by x33a on 2010-02-07
Take a look here:

[http://ubuntuforums.org/showthread.php?t=875430](http://ubuntuforums.org/showthread.php?t=875430)

---

### Post by Nick43092 on 2010-02-07
Awesome. Thanks a ton.

---

