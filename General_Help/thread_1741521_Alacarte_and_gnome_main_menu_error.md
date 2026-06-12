---
title: "Alacarte and gnome main menu error"
date: 2011-04-28
forum: General Help
---

### Post by aldais on 2011-04-28
Hi folks, 

Requesting for help here,

I was helping to fix a friend's Maverick installation today. When I was running "alacarte" to edit the main menu of the gnome panel, the application hangs up and I have to kill the applications. Afterwards, the "Applications" menu becomes inaccessible while the "Places" and "System" menus are still accessible. Apparently, all the applications are not autodetected when I do the "alt-f2" a.k.a. "run application" tool.

When running "alacarte" from the terminal,
the output is as shown below :

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
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: junk after document element: line 28, column 2

I'd really appreciate if you kind folks here can help me and my unfortunate friend. Many thanks from Singapore.

---

### Post by KegHead on 2011-04-28
Hi!

Have you tried to install via;

system...admin..synaptic

or

sudo apt-get upgrade

sudo apt-get install alacarte -f

KegHead

---

### Post by mc4man on 2011-04-28
You could try opening  up home folder (view - show hidden files) > .config > menus and deleting the applications.menu file

---

### Post by aldais on 2011-04-30
Dear folks,
Thanks for the replies, and apologies for the late response. I havent got the chance to help the mentioned friend yet, but will try to do soon. Thanks again, for the replies. I'll get back here if those do not solve the problem.

---

