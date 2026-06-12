---
title: "Main Menu doesn't launch in Karmc"
date: 2010-03-15
forum: General Help
---

### Post by levells on 2010-03-15
I installed a few programs last night but I didn't like how they were arranged in the menu. I went to System -> Preferences -> Main Menu but nothing launched. Anyone have this happen to them before?

---

### Post by plucky on 2010-03-16
> **levells said:**
> I installed a few programs last night but I didn't like how they were arranged in the menu. I went to System -> Preferences -> Main Menu but nothing launched. Anyone have this happen to them before?

From a terminal ```
alacarte
``` post any errors.

Or Right click on **Applications** and select **Edit Menus**

Good Luck

---

### Post by levells on 2010-03-16
```
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
IOError: [Errno 13] Permission denied: '/home/levells/.config/menus/applications.menu'

```

---

### Post by prodigy_ on 2010-03-16
> **levells said:**
> ```
IOError: [Errno 13] Permission denied: '/home/levells/.config/menus/applications.menu'

```
Seems to be the culprit. Try this: ```
chmod 644 /home/levells/.config/menus/applications.menu
```

---

### Post by levells on 2010-03-16
Trying that gives me this:
```
chmod: cannot access `/home/levells/.config/menus/applications.menu': Permission denied
```
And when I try it with sudo, it doesn't show anything. I tried alacarte to see what comes up and it's the same as before.

---

### Post by prodigy_ on 2010-03-16
> **levells said:**
> Trying that gives me this:
```
chmod: cannot access `/home/levells/.config/menus/applications.menu': Permission denied
```
And when I try it with sudo, it doesn't show anything. I tried alacarte to see what comes up and it's the same as before.

I see. Looks like this file ownership has changed for some reason. If so, the solution is as follows:

# The first command will output a <number>, most probably 1000.
```
id -u
```
# If needed, change 1000:1000 in the next command to <number>:<number>, according to "id -u" result.
```
sudo chown 1000:1000 /home/levells/.config/menus/applications.menu
```
```
chmod 644 /home/levells/.config/menus/applications.menu
```

---

### Post by levells on 2010-03-16
The number was 1000 but still no results.
The only way I can get to it is with 'sudo alacarte' from the terminal. I tried changing the command for main menu that way by adding sudo to it but I still can't access it normally, from preferences.

```
levells@levells-laptop:~$ id -u
1000
levells@levells-laptop:~$ sudo chown 1000:1000 /home/levells/.config/menus/applications.menu
levells@levells-laptop:~$ chmod 755 /home/levells/.config/menus/applications.menu
chmod: cannot access `/home/levells/.config/menus/applications.menu': Permission denied
```

---

### Post by plucky on 2010-03-16
Post output of ```
ls -l ~/.config/menus/applications.menu
```

---

### Post by levells on 2010-03-16
```
levells@levells-laptop:~$ ls -l ~/.config/menus/applications.menu
ls: cannot access /home/levells/.config/menus/applications.menu: Permission denied
levells@levells-laptop:~$ sudo ls -l ~/.config/menus/applications.menu
[sudo] password for levells: 
-rwxr-xr-x 1 levells levells 233 2010-03-16 13:22 /home/levells/.config/menus/applications.menu

```

---

### Post by wojox on 2010-03-16
That's your problem. You shouldn't have to sudo it. It looks like root owns it. It should be **-rw-r--r--**

---

### Post by prodigy_ on 2010-03-16
> **wojox said:**
> That's your problem. You shouldn't have to sudo it. It looks like root owns it. It should be **-rw-r--r--**

Nah. Execution bit doesn't change much. It's not necessary (so chmod 644 can be ised instead of chmod 755), but the file should still be accessible. And if it were owned by root, ls -l would show that.

---

It's really weird... Hmm. Try this:

1. Open nautilus first and browse to **/home/levells/.config/menus** folder.

2. In terminal: ```
sudo mv /home/levells/.config/menus/applications.menu /home/levells/.config/menus/applications.menu.bak
```

3. In nautilus: create an empty document named **applications.menu**

4. Open both **applications.menu** and **applications.menu.bak** in gedit and copypaste all text from the old file to the new one. Save changes.

---

### Post by levells on 2010-03-16
The 'Menus' folder was restricted,  I had to launch nautilus with sudo to see inside it.
I don't have permission to save inside that directory without using sudo.
Nothing's changed, still unable to launch normally.
And if it helps, here's the contents of the file:
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
    <Name>Applications</Name>
    <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>
```
Also, the properties of applications.menu list root as owner (read/write) and group (read-only).

---

### Post by wojox on 2010-03-16
> **prodigy_ said:**
> Nah. Execution bit doesn't change much. It's not necessary (so chmod 644 can be ised instead of chmod 755), but the file should still be accessible. And if it were owned by root, ls -l would show that.

Ahh, forgot about that. My mistake.

---

### Post by prodigy_ on 2010-03-16
Heh. Alright, it's time for an ol' good nuclear strike. ;-) This will reset ownership for **everything** in your home folder (return it back to you):
```
sudo chown -R 1000:1000 ~
```

---

### Post by levells on 2010-03-16
Lol. I like the phrasing. Unfortunately, my laptop isn't making this easy. Got anything else?
```
levells@levells-laptop:~$ sudo chown -R 1000:1000 ~
[sudo] password for levells: 
chown: cannot access `/home/levells/.gvfs': Permission denied
levells@levells-laptop:~$ 
```

On the bright side, Main Menu launches normally. :)
Is the folder listed above anything I should worry about?

---

### Post by prodigy_ on 2010-03-16
~/.gvfs is a virtual directory inaccessible for root. This is by (rather poor) design so ignore this message.

---

### Post by levells on 2010-03-16
Okay. Many thanks :)

---

