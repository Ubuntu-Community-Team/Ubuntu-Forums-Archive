---
title: "GNOME Applications Menu Editor"
date: 2006-01-24
forum: General Help
---

### Post by AirIntake on 2006-01-24
I can't seem to run the Applications Menu Editor anymore. When I try to, it puts a item on the program bar that says 'Starting Applications Menu Editor', but then that just goes away and the menu editor never does start. I know it used to work. Also, since the editor isn't working, how can I manually remove launchers from the applications menu?

---

### Post by endersshadow on 2006-01-24
First off, try these commands in the terminal:

```
sudo killall smeg
sudo -k
smeg
```

If that does not work, your shortcuts are in /usr/share/applications as *.desktop files.  You can manually remove them there.  If you get a permission denied error, use sudo.  However, the above code should work just fine for you.

---

### Post by AirIntake on 2006-01-24
```
brad@BitchBoxIV:~$ sudo killall smeg
Password:
smeg: no process killed
brad@BitchBoxIV:~$ sudo -k
brad@BitchBoxIV:~$ smeg
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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1030, in __addFiles
    self.__addFiles(dir, os.path.join(subdir,item), prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 26-28: invalid data

```

That's what I got. The menu editor still won't load. Thanks for the help so far though!

---

### Post by endersshadow on 2006-01-24
Try:

```
sudo apt-get remove smeg
sudo apt-get install smeg
```

It seems that your smeg has got errors in it all over the place...this is just reinstalling it...

---

### Post by AirIntake on 2006-01-24
The remove and install seemed to work fine with no errors, but the menu editor still won't start up. I have no idea why this happened.......

---

### Post by nominal on 2006-01-24
What error do u get when you run the menu edditor from the terminal?

---

### Post by AirIntake on 2006-01-24
when I run "smeg" (I'm assuming that's the menu editor command) in the terminal, I get this error string:
```
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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1030, in __addFiles
    self.__addFiles(dir, os.path.join(subdir,item), prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 26-28: invalid data
```

---

### Post by Perfect Storm on 2006-01-24
Go to /home/<username>/.config 

You'll see two folders there 'menues' and 'smeg' back them up and remove the two files. Otherwise try diffrent combination of only removing one of them.

killall gnome-panel

---

### Post by AirIntake on 2006-01-24
I tried removing one, the other, then both (doing killall gnome-panel each time) but I get the exact same error messages when I try to start smeg.

---

### Post by AirIntake on 2006-01-26
Is there anything that I can do or do I have to reinstall Ubuntu?

---

### Post by AirIntake on 2006-01-27
Great, I guess I'll reinstall the whole thing. It's too bad Ubuntu doesn't have a system restore like XP.....

---

### Post by bugmenot on 2006-01-27
Ya 
there is an issue with the Gnome Menu Editor

It sucks!

i remember when i searched a lot on this issue
there was a python library that i reinstalled(apt-get install)
and that fixed the menu editor

Now i just checked and yeah even my menu editor is not functioning

i hope you can search which python library has to be reinstalled

bai

---

### Post by bugmenot on 2006-01-27
looking at the error output you posted 

i remembered what python lib i had reinstalled

go to synaptic search
menu-xdg

reinstall it

warning: the debian menu sometimes disappears after this is done
and i do do it often enough


bai

---

### Post by AirIntake on 2006-01-27
THANK YOU THANK YOU THANK YOU!!!!!!

That did it alright!

A moderator should pin this or something, as I'm sure other people have experienced this.

---

### Post by s_spiff on 2006-01-28
talking of System Restore, I think those guys should make something like it , I messed up installation of FF1.5 the 1st time I did it, I couldn't do anything, had to reinstall all over again.

---

### Post by phyziks on 2006-01-30
[QUOTE=AirIntake]THANK YOU THANK YOU THANK YOU!!!!!!

That did it alright!

A moderator should pin this or something, as I'm sure other people have experienced this.[/QUOTE]

x2  I had this same issue, and I searched for 2 days before happening upon this fix.  Thanks.:-D

---

