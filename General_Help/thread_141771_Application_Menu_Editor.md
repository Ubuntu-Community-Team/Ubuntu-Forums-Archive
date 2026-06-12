---
title: "Application Menu Editor"
date: 2006-03-09
forum: General Help
---

### Post by nahas on 2006-03-09
Hi all,
      i installed few softwarwes with automatix,but then the appication menu editor doesnt seem to work,i doesnt open up.Pls help me out with this.also is there any way i can make the appication menu look more compactand neat coz as of now if u open the applcation menu it covers the entire screen... looks wierd..
tnx

---

### Post by aysiu on 2006-03-09
Can you go to Applications > Accessories > Terminal, type ```
smeg
``` and then post the output here?

---

### Post by nahas on 2006-03-10
this is the output of the command smeg,please go through
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __init__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/dvdrip.desktop'

---

### Post by aysiu on 2006-03-10
It's a mystery.

I popped one of your errors into [a Google search](http://www.google.com/search?hl=en&q=File+%22%2Fusr%2Flib%2Fsmeg%2FMenuHandler.py%22%2C+line+56%2C+in+__init__&btnG=Google+Search).

There were only two unique results. One was a Ubuntu Forums thread about pointing SMEG to Python 2.4 instead of 2.3. You're already at 2.4, so that's a non-issue.

The other didn't seem to have an answer.

---

### Post by fossill on 2006-03-10
was having the same problems as you.  I didn't think to throw it in terminal.

It's a permissions problem.  sudo -s smeg 

it works a charm.  It's weird, I have installed, uninstalled, tried different packages, etc, and finally you guys helped me figure it out.

---

