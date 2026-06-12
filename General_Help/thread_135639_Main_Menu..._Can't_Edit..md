---
title: "Main Menu... Can't Edit."
date: 2006-02-24
forum: General Help
---

### Post by ephman on 2006-02-24
hi,

ok this is a strange problem.  on my old computer no problem i can edit the main menu, but on my new one i can't seem to get that to work.  i right click on the little ubuntu logo, select edit menu, and then a new window opens on the toolbar that says "starting applications menu editor", and then nothing.  any ideas?

thanks,
ephman

---

### Post by SavageBeginner on 2006-02-24
Type this into the terminal, and see if it gives you any error messages:```
smeg
```

---

### Post by ephman on 2006-02-24
thanks,

here's the output.  looks like there is an error, but i'm not sure what to do about.


ephman@wintermute:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init_ _
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNot OnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNot OnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntr ies
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __ini t__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse
    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/dvdrip.desktop'



thanks,
ephman

---

### Post by SavageBeginner on 2006-02-24
Looks like you don't have read permission for /usr/share/applications/dvdrip.desktop
This should fix it:```
sudo chmod a+r /usr/share/applications/dvdrip.desktop
```

---

### Post by ephman on 2006-02-24
thumbs up... did the trick thank you very much.

be well,
ephman

---

### Post by magomago on 2006-02-26
Hi I have the same problem.  I tried to check my output for anything similar but I can't find anything, perhaps do you guys see what is the problem?


amarry@cv080006:~$ smeg
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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
    __parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 575, in __parse
    __parseMergeFile("applications.menu", child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 742, in __parseMergeFile
    __mergeFile(os.path.join(p,rel_file),child,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 785, in __mergeFile
    __parse(child,filename,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 586, in __parse
    __parseDefaultMergeDirs(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 762, in __parseDefaultMergeDirs
    __parseMergeDir(os.path.join(dir, "menus", basename + "-merged"), child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 755, in __parseMergeDir
    __mergeFile(os.path.join(value, item), child, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 785, in __mergeFile
    __parse(child,filename,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 571, in __parse
    parent.Rules.append(Rule(child.tagName, child))
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 284, in __init__
    self.compile()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
    exec("""
  File "<string>", line 6
    elif :
         ^

---

### Post by magomago on 2006-02-26
bump

---

### Post by shapht on 2006-02-26
Thanks for the tip. I had a similiar issue.

---

### Post by hero2zero on 2006-03-21
[QUOTE=magomago]Hi I have the same problem.  I tried to check my output for anything similar but I can't find anything, perhaps do you guys see what is the problem?


amarry@cv080006:~$ smeg
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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
    __parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 575, in __parse
    __parseMergeFile("applications.menu", child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 742, in __parseMergeFile
    __mergeFile(os.path.join(p,rel_file),child,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 785, in __mergeFile
    __parse(child,filename,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 586, in __parse
    __parseDefaultMergeDirs(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 762, in __parseDefaultMergeDirs
    __parseMergeDir(os.path.join(dir, "menus", basename + "-merged"), child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 755, in __parseMergeDir
    __mergeFile(os.path.join(value, item), child, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 785, in __mergeFile
    __parse(child,filename,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 571, in __parse
    parent.Rules.append(Rule(child.tagName, child))
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 284, in __init__
    self.compile()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
    exec("""
  File "<string>", line 6
    elif :
         ^[/QUOTE]

I just had the same thing happen to me today.  I've tried removing and reinstalling smeg with the same results...  Any one?

---

