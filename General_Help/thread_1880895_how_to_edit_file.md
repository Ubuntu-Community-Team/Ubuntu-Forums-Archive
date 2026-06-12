---
title: "how to edit file"
date: 2011-11-14
forum: General Help
---

### Post by jackj on 2011-11-14
I'm sure this is very basic, but I don't understand.  I'm using 10.04.

I need to modify a file which is located in /etc.  The file name is modules.
So I go to etc and list it, and I don't see a file by the name of modules.
So I think, well, maybe I'm supposed to create one if it doesn't exist.

So I type gedit modules.  And guess what?  A file pops up.  I think, well, that's nice, I'll just edit it as I need to.  But I soon find out the file is read only.  So how do I add a line to /etc/modules?

---

### Post by sum1nil on 2011-11-14
Files in /etc are read only unless you use 'sudo <editor> <filename>':
'sudo gedit /etc/modules'.

This opens it with root permissions and you should be able to write to it.

:popcorn:

---

### Post by stinkeye on 2011-11-14
```
gksudo gedit /etc/modules
```

You might also look at installing 
```
nautilus-gksu
```
Adds an **Open as administrator** item to the nautilus right click menu.
Then you can just browse to the file and right click on it.
Only edit files as root if your confident in the reliability of the info
you are being given.

Edit:looks like it's a hot topic to answer.

---

### Post by carranty on 2011-11-14
Since /etc/modules is not in your /home directory you need superuser access to modify it.

*sudo gedit /etc/modules*

will do the trick.  I'd suggest creating  a backup before modifying it though in case you do something silly
[I]
sudo cp /etc/modules /etc/modules_BAK[/I]

---

### Post by e79 on 2011-11-14
use gksu in front of your command (you will be prompted for your root password):

```
gksu gedit /Folder/File
```

EDIT*

Looks like I answered just a couple seconds too late lol

---

### Post by eltonw on 2011-11-14
You need to have **root** (superuser) priviliiges to edit the file. So from a console prompt, you would do:
sudo gedit /etc/modules
You must then supply your password to "unlock" the file for editing.

---

### Post by jackj on 2011-11-14
Thank you.

---

### Post by ajgreeny on 2011-11-14
PLEASE, PLEASE get into the habit of using **gksu** not **sudo** to open GUI applications with root privileges.  You should only use sudo for terminal utilities and applications

You would actually be OK using sudo with gedit, but some GUI apps will not work in that way, and can even cause problems and lock you out of the system.

See Root-suso in my signature for all the details.

---

