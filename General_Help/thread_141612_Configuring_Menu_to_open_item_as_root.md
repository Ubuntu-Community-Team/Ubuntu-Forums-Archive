---
title: "Configuring Menu to open item as root"
date: 2006-03-08
forum: General Help
---

### Post by Burgresso on 2006-03-08
Hi yall.

I noticed that the Application Menu Editor won't start - I try to open via the menu item. I then tried to open it via the commandline, and I discovered it needs to be opened via sodu root. How can I edit a menu item so it opens it as root?

Thanks in advance!

Oh, and does anyone know an easy way to add dividers to Gnome panes?

\\:D/

---

### Post by Burgresso on 2006-03-08
PS It also doesn't open when I try get to it by right cliking on the menu.

---

### Post by thnogueira on 2006-03-08
Did you try 

gksudo <<command>>?

But it seems strange to me that you need to run smeg as su...

---

### Post by Burgresso on 2006-03-08
I agree, something is going on here...
This what happens when I type "smeg" in the commandline:

>  File "/usr/bin/smeg", line 562, in ?
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
IOError: [Errno 13] Permission denied: '/usr/share/applications/avidemux.desktop

---

### Post by thnogueira on 2006-03-08
Have you checked the
/usr/share/applications/avidemux.desktop 
permissions?

Maybe you should change it (as root)
Try to > chmod 755 /usr/share/applications/avidemux.desktop, 
if doesn't work 777 (maybe a security issue?).
if you always use the computer as the same user, you can chenge the file owner instead:
> chown user:user /usr/share/applications/avidemux.desktop

---

### Post by Burgresso on 2006-03-08
Brilliant thnogueira!

I tried this

>  chmod 755 /usr/share/applications/avidemux.desktop

And it worked! Thank you very much!

---

