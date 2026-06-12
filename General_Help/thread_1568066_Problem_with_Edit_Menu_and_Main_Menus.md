---
title: "Problem with Edit Menu and Main Menus"
date: 2010-09-04
forum: General Help
---

### Post by badex on 2010-09-04
Hi there. I've  been using Ubuntu 10.04 for the last few days and I love it. However, I have encountered a slight problem- I cannot edit the menu system. 

When I click on Main Menus under Preferences nothing happens. When I right click on the menus and select Edit Menus no dialogue box appears. I can fix this by removing Main Menus from the system. The thing is I want to add programs, ones that are installed but not showing, under Applications. At the moment there is no way of doing this.

Any ideas anyone?

---

### Post by mc4man on 2010-09-04
Not sure why you can't do what you're trying.
See if this works or if not produces a message of interest

In a terminal (Applications - Accessories) enter and run this

```
alacarte 
```

---

### Post by drs305 on 2010-09-04
Menu editing is done by *alacarte* in 10.04 I believe. It's in the "main" repository so it should be installed. You could open Synaptic, highlight "alacarte", right click and choose to reinstall, then "apply" to see if that fixes it.

---

### Post by drs305 on 2010-09-04
Menu editing is done by *alacarte* in 10.04 I believe. It's in the "main" repository so it should be installed. You could open Synaptic, highlight "alacarte", right click and choose to reinstall, then "apply" to see if that fixes it (or run alacarte from the terminal).

---

### Post by badex on 2010-09-04
> **mc4man said:**
> Not sure why you can't do what you're trying.
See if this works or if not produces a message of interest

In a terminal (Applications - Accessories) enter and run this

```
alacarte 
```


When I try and launch Alacarte from the terminal this is what I get...
:confused:
```
alsander@ubuntu:~$ alacarte
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
IOError: [Errno 13] Permission denied: '/home/alsander/.config/menus/applications.menu'

```

---

### Post by badex on 2010-09-04
I removed Alacarte and installed it again. I keep getting the same error message [Errno 13] Permission denied: '/home/alsander/.config/menus/applications.menu'. When I checked permissions on the menus folder it says the owner is root. Do I need to change this?

---

### Post by DarthScape on 2010-09-04
maybe sudo alacarte?

---

### Post by badex on 2010-09-04
> **DarthScape said:**
> maybe sudo alacarte?

That does the trick.Thanks to everyone. I'm surprised at how fast those responses were! :D

---

### Post by drs305 on 2010-09-04
badex,

Actually, things may still not be quite correct. You *should* be able to run "alacarte" as a normal user (to be able to modify your own menus); the file .config/menus/applications.menu should belong to you, the user, and not root.

You might want to run the following command to see if you have other files in your /home folder that belong to "root". Normally none of the files in your home folder should be owned by root.
```
ls -la ~/ | grep root
```

---

### Post by badex on 2010-09-04
> **drs305 said:**
> badex,

Actually, things may still not be quite correct. You *should* be able to run "alacarte" as a normal user (to be able to modify your own menus); the file .config/menus/applications.menu should belong to you, the user, and not root.

You might want to run the following command to see if you have other files in your /home folder that belong to "root". Normally none of the files in your home folder should be owned by root.
```
ls -la ~/ | grep root
```

Hi drs305,

I was able to change the permissions on the folders by pressing Alt+F2 and then entering 
gksudo nautilus. As you might have guessed, I have little experience using the terminal. Now I can launch alacarte from the System menu. I then entered your code.

```
alsander@ubuntu:~$ ls -la ~/ | grep root drwxr-xr-x  3 root     root       4096 2010-09-03 00:12 ..
```

I'm not sure what this means? BTW thanks for your time. I appreciate it.:)

---

### Post by drs305 on 2010-09-04
> **badex said:**
> I'm not sure what this means? BTW thanks for your time. I appreciate it.:)

The first part of the command lists the files/folders in your home folder. The "-la" allows it to show hidden files and attributes. The "grep" portion says to take the results and only display returns with contain the word "root".

So the command (in general terms) asks the system to show all files in your home folder, including hidden files/folders which are owned by root. 

If you had dozens of files displayed it would have meant that somehow your file permissions had been changed, probably by the improper use of the "chown" (change ownership) command. As stated earlier, generally all the files in your home folder should be owned by you so you wouldn't expect to get any returns with "grep root". If you had run the command with "| grep alsander" you would have seen lots of returns.

As to what happened when you ran the original command and it generated the error message:
You ran "alacarte" as non-root so it tried to change the configuration file in your home folder (/home/alsander/.config/menus/applications.menu). Since at the time it wasn't owned by you, but by root, it wouldn't let you change the file.

When you then ran the command as root, it allowed the *root* menu configuration file to be changed. It actually didn't change the file in your /home folder, but acted on a file in /root/.config/menus/

When running the alacarte command as root, any changes you made would have been reflected in the menus viewed by any other user (a universal change) as opposed to making a change only viewable when you are logged in.

---

### Post by calin_ionut on 2010-10-18
This is not a fix....i am getting the same error! The menu should be edited by user too, not only by the root.

---

