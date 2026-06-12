---
title: "I can not edit the menu"
date: 2010-07-22
forum: General Help
---

### Post by josephp on 2010-07-22
I can not edit the menu in Ubuntu 10.04. This is happing on two different computers. I click on Main Menu and right click on the menu and click edit menu it does nothing. When I run alacarte in the terminal i get this

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
IOError: [Errno 13] Permission denied: '/home/badass/.config/menus/applications.menu'

I started using Ubuntu Tweak on both systems. Could that have cause it.

---

### Post by ridgeland on 2010-07-24
I had a user that could not edit the menu.  The user had run the partition out of space.  The sad part was GBs and GBs were in "trash" but Gnome/Nautilus blew up instead of asking about emptying the trash.
Looks like your issue is permissions though.  User badass cannot edit his/her own files. Try
$ sudo chown badass /home/badass/.config/menus/applications.menu
If that doesn't fix it also try:
$ sudo chmod -R 666 /home/badass/.config/*
study chown and chmod
$ man chown
$ man chmod
With a user name of badass it's not surprising no one is helping you.

---

### Post by WorMzy on 2010-07-24
I don't know how Ubuntu tweak does it's stuff, but did you run it with "sudo" at some point? Because using sudo to run a graphical application can really mess up your permissions in your home folder. Use gksu or gksudo instead, they're the "safe" way to use graphical applications as root.

---

