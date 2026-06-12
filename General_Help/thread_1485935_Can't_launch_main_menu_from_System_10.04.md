---
title: "Can't launch main menu from System 10.04"
date: 2010-05-17
forum: General Help
---

### Post by BigBaka on 2010-05-17
After a fresh install of Ubuntu 10.04 and having installed a bunch of apps, I wanted to adjust the main menu but have found that I can't actually launch the main menu from the System / Preferences menu. Nothing happens. Tried typing the Main Menu command alacarte into terminal, and I get the following read out.


jvc@CF1:~$ alacarte
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
IOError: [Errno 13] Permission denied: '/home/jvc/.config/menus/applications.menu'
jvc@CF1:~$ 

Any idea how to get main menu up and running again?

---

### Post by D3jan on 2010-05-17
remove the corrupted file
Code:~/.config/menus/application.menu 
maybe is old post but it can help [http://ubuntuforums.org/showthread.php?t=639457](http://ubuntuforums.org/showthread.php?t=639457)

---

### Post by BigBaka on 2010-05-17
Thanks D3jan
But how should I do that? I can't go through the GUI interface as I can't get access into the menus folder.

Can you please post the terminal script. Sorry, I'm still a noob on this stuff.

---

### Post by BigBaka on 2010-05-26
> **D3jan said:**
> remove the corrupted file
Code:~/.config/menus/application.menu 
maybe is old post but it can help [http://ubuntuforums.org/showthread.php?t=639457](http://ubuntuforums.org/showthread.php?t=639457)



Had a look through the post and used gksu nautilus to try and remove the file. Alas, got into my ~/.config/menus directory and there was no application.menu file or folder. In fact the only thing in the menus folder was another folder called applications-merged

---

### Post by BigBaka on 2010-05-26
Ha, Got it!

It was a permissions issue. Fixed it with this.


```
sudo chown -R $USER ~/.config ~/.local
```

---

### Post by gadolinio on 2010-05-27
> **BigBaka said:**
> Ha, Got it!

It was a permissions issue. Fixed it with this.


```
sudo chown -R $USER ~/.config ~/.local
```

Please remember to mark the thread as SOLVED if your problem is fixed :)

---

