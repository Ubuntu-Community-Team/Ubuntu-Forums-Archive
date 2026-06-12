---
title: "System&gt;Preferences&lt;Main Menu won't open"
date: 2011-01-27
forum: General Help
---

### Post by layers on 2011-01-27
I just wanted to modify s shortcut, but it just did not open. I'm not sure if this is supposed to help or hurt anyone, but does anyone see any problems?
```
ibo@ibo-laptop:~$ alacarte
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
IOError: [Errno 13] Permission denied: '/home/ibo/.config/menus/applications.menu'
ibo@ibo-laptop:~$ cd ~/.config/
```

---

### Post by Smart Viking on 2011-01-27
do
```
chmod 644 /home/ibo/.config/menus/applications.menu
```

And try again.

---

### Post by layers on 2011-01-27
```
ibo@ibo-laptop:~/Downloads$ sudo chmod 644 /home/ibo/.config/menus/applications.menu
chmod: cannot access `/home/ibo/.config/menus/applications.menu': No such file or directory
ibo@ibo-laptop:~/Downloads$
```

---

### Post by wojox on 2011-01-27
What does this return:

```
ls -al .config/menus/
```

---

### Post by layers on 2011-01-27
> **wojox said:**
> What does this return:

```
ls -al .config/menus/
```
```
ibo@ibo-laptop:~/Downloads$ ls -al .config/menus/
ls: cannot access .config/menus/: No such file or directory
ibo@ibo-laptop:~/Downloads$ 
```

---

### Post by wojox on 2011-01-27
> **layers said:**
> ```
ibo@ibo-laptop:~/Downloads$ ls -al .config/menus/
ls: cannot access .config/menus/: No such file or directory
ibo@ibo-laptop:~/Downloads$ 
```

Your in Downloads. Try this:

```
ls -al /home/ibo/.config/menus/
```

---

### Post by layers on 2011-01-27
> **wojox said:**
> Your in Downloads. Try this:

```
ls -al /home/ibo/.config/menus/
```
sorry, multitasking (not probably doing even one task properly, though).
```
ibo@ibo-laptop:~$ ls -al /home/ibo/.config/menus/
ls: cannot access /home/ibo/.config/menus/.: Permission denied
ls: cannot access /home/ibo/.config/menus/..: Permission denied
ls: cannot access /home/ibo/.config/menus/applications-merged: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
d????????? ? ? ? ?                ? applications-merged
ibo@ibo-laptop:~$ 
```

---

### Post by Smart Viking on 2011-01-28
```
sudo chown -R ibo:ibo /home/ibo/.config/menus/
```
Then report the output of
```
ls -al  /home/ibo/.config/menus/
```

---

### Post by layers on 2011-01-28
> **Smart Viking said:**
> ```
sudo chown -R ibo:ibo /home/ibo/.config/menus/
```Then report the output of
```
ls -al  /home/ibo/.config/menus/
```
I do not know what I (you) did, but thanks. It worked.

```
ibo@ibo-laptop:~$ sudo chown -R ibo:ibo /home/ibo/.config/menus/
[sudo] password for ibo: 
ibo@ibo-laptop:~$ ls -al /home/ibo/.config/menus/
total 12
drwxrw-rw-  3 ibo ibo 4096 2011-01-26 23:08 .
drwxr-xr-x 13 ibo ibo 4096 2011-01-27 21:33 ..
drwxrw-rw-  2 ibo ibo 4096 2011-01-26 23:08 applications-merged
ibo@ibo-laptop:~$ 

```

---

