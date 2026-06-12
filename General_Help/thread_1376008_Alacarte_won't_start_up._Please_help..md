---
title: "Alacarte won't start up. Please help."
date: 2010-01-08
forum: General Help
---

### Post by Bazraby-Ziha on 2010-01-08
When I try to start alacarte from the shell, I get:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 48, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

The reason I start from the shell is because I noticed that it would crash after starting up in system monitor. 
This problem started after I tried to remove a program from the list which had already been manually removed.
When this program was unchecked, the list went completely blank. I tried to revert the list, but it didn't work.
Is there any hopes of repair?

I appreciate any help you can offer me.

---

### Post by RedSingularity on 2010-01-08
First lets completely remove it from your system.

sudo apt-get autoremove --purge alacarte

If that command doesn't work for some reason post the output here.

---

### Post by Bazraby-Ziha on 2010-01-08
The command completed successfully.

---

### Post by RedSingularity on 2010-01-09
Ok good, that means it was successfully removed.  Of course hidden files with settings may exist.  You need to search for them and delete any files that are left.

sudo find / -name alacarte

and

sudo find / -name .alacarte

---

### Post by Bazraby-Ziha on 2010-01-10
I executed the commands and no output was shown for either. Does that mean it automatically found the files and deleted them, or does it mean that files don't exist?

---

### Post by Tahakki on 2010-01-10
None exist. :)

Now you could re-install:

```
sudo apt-get install alacarte
```

Or just search for it in the software store.

---

### Post by Bazraby-Ziha on 2010-01-10
Ok. It's installed, but I still have this error when I try to run it:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 48, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

---

### Post by psrivats on 2010-01-11
I am having issues with alacarte as well. I am running 9.10 on a thinkpad T60. Removing and reinstalling has no change, still get the same errors:

```
psrivats@Bender:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 63, in __loadMenus
    self.save(True)
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 67, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/psrivats/.config/menus/applications.menu'
psrivats@Bender:~$ 

```

I checked the file permissions of the ~/.config folder and noticed and menu and sufolders/files are owned by root:
```
psrivats@Bender:~/.config$ ls -la
total 64
drwxr-xr-x 13 psrivats psrivats 4096 2010-01-10 14:10 .
drwxr-xr-x 46 psrivats psrivats 4096 2010-01-11 01:25 ..
drwx------  2 psrivats psrivats 4096 2010-01-10 14:57 autostart
drwx------  3 psrivats psrivats 4096 2010-01-10 00:43 compiz
drwx------  2 psrivats psrivats 4096 2010-01-10 14:06 enchant
drwxr-xr-x  3 psrivats psrivats 4096 2010-01-09 23:26 gnome-disk-utility
drwxr-xr-x  3 psrivats psrivats 4096 2010-01-09 23:25 gnome-session
drwx------  2 psrivats psrivats 4096 2010-01-11 00:44 gtk-2.0
drwxr-xr-x  3 psrivats psrivats 4096 2010-01-10 14:10 indicators
[COLOR="Red"]drwx------  3 root     root     4096 2010-01-11 01:33 menus[/COLOR]
drwxr-xr-x  5 psrivats psrivats 4096 2010-01-10 00:48 Screenlets
drwxr-xr-x  4 psrivats psrivats 4096 2010-01-10 17:39 smplayer
-rw-r--r--  1 psrivats psrivats 2954 2010-01-10 05:49 Trolltech.conf
-rw-------  1 psrivats psrivats  632 2010-01-09 23:25 user-dirs.dirs
-rw-r--r--  1 psrivats psrivats    5 2010-01-09 23:25 user-dirs.locale
drwxr-xr-x  5 psrivats psrivats 4096 2010-01-10 06:07 xmms2

psrivats@Bender:~/.config$ ls -l menu
ls: cannot access menu: No such file or directory

```

Changing the permissions using chown -R fixed the issue. The command I used was:

```
sudo chown -R <username>:<username> menus
```

Hope this helps.

---

### Post by Bazraby-Ziha on 2010-01-11
I checked the permissions on the menus folder in ~/.config using ***ls -la***, but I already have ownership of all files and subfolders.




Edit: I inspected the menus folder in ~/.config and found out that the applications.menu file is empty. Does anyone know how to automatically add installed programs to the file? I really don't want to have to add them manually. (^.^;)

Thanks again for the help. :-)

---

