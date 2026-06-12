---
title: "??? /etc/apt/sources.list  ???"
date: 2009-11-25
forum: General Help
---

### Post by Nailox on 2009-11-25
where is the /etc/apt/sources.list file ? me try search and me cannot find the file... and how to add a line to it and where ? at the end ? running karmic koala. thanks . :popcorn:

---

### Post by x C0MMAND0 x on 2009-11-25
Try the following.

```
sudo gedit /etc/apt/sources.list
```

That will bring up an editor and then you can edit it from there.

---

### Post by audiomick on 2009-11-25
Hallo.
If you open a terminal
files > accessories > terminal

and type in

```
sudo gedit /etc/apt/sources.list
```

you will be asked for a password, which is the one you log on with, and when you type it in and editor (gedit) will open with the file in it.

The sudo bit is to give you root privileges. As far as I know, the file belongs to root, and you can't edit it as a normal user.

Be careful doing this.

You can do the same using the graphical package manager.

open the synaptic package manager
system > system administration > synaptic package manager

the second tab, "other software" probably. don't know for sure as mine is in German.

at the bottom left is a button "add"
in the window that opens, type in what you would have added to the file.

I think you will need to add an authentification key. That is done on the 4th. tab.

---

### Post by Nailox on 2009-11-25
wow 10x guys for the fast response - I love this forum :)

---

### Post by louieb on 2009-11-25
Better safe than sorry. Using sudo with a graphical program can screw your user id up to the point you can't login to the graphical desktop. .  use gksudo instead. 
```
gksudo gedit /etc/apt/sources.list
```

---

