---
title: "open a file with command line"
date: 2010-05-29
forum: General Help
---

### Post by lovo on 2010-05-29
Hello
is it possible to open a file with a terminal without specifying the application it will use ? In fact I mean what is the equivalent of the double click on the file manager for a terminal.
thanks
swan

---

### Post by dcstar on 2010-05-30
> **lovo said:**
> Hello
is it possible to open a file with a terminal without specifying the application it will use ? In fact I mean what is the equivalent of the double click on the file manager for a terminal.
thanks
swan

No.

---

### Post by ryan858 on 2010-05-30
Nope. Gotta use a command to open anything.

There are ways, however, to make the command simpler if it's a lengthy command with switches and whatnot... You can make scripts or use symlinks... For example, I've linked *gnome-system-monitor* to *sysmon.* And I've made a script named *get*:
```

#!/bin/bash
sudo apt-get install $1

```So I just do:
**$ get <package name>**
to install something.

---

### Post by diesch on 2010-05-30
Use
```
 xdg-open some_file
``` to open a file with the standard application for its file type.

---

### Post by lovo on 2010-05-30
> **diesch said:**
> Use
```
 xdg-open some_file
``` to open a file with the standard application for its file type.

good job!

---

### Post by VCoolio on 2010-05-30
xdg-open will listen to the default applications set with (g)alternatives; you could also use kde-open (gnome-open in, well, gnome / ubuntu) to use defaults that are used in dolphin / nautilus (stored in ~/.local/share/applications/mime-apps.list I think).

---

### Post by inso_741 on 2010-05-30
> **ryan858 said:**
> Nope. Gotta use a command to open anything.

There are ways, however, to make the command simpler if it's a lengthy command with switches and whatnot... You can make scripts or use symlinks... For example, I've linked *gnome-system-monitor* to *sysmon.* And I've made a script named *get*:
```

#!/bin/bash
sudo apt-get install $1

```So I just do:
**$ get <package name>**
to install something.

It dosent work w/o sh
eg: sh get pkg-name
how do you do it w/o it?

---

### Post by geirha on 2010-05-30
> **inso_741 said:**
> It dosent work w/o sh
eg: sh get pkg-name
how do you do it w/o it?

Put it in ~/bin/ and make it executable

```

mkdir -vp ~/bin       # create the dir if it doesn't exist
mv -v get ~/bin       # move the script to ~/bin
chmod -v +x ~/bin/get # make it executable

```
After issuing those three commands, log out and back in again. Then you should be able to run it with just
```
get package-name
```

If you change the script to do 
```
sudo apt-get install "$@"
```
instead, you can install multiple packages at the same time btw. E.g. «get hello sl»

---

### Post by inso_741 on 2010-05-30
@geirha: thanx

---

### Post by diesch on 2010-05-30
> **VCoolio said:**
> xdg-open will listen to the default applications set with (g)alternatives; you could also use kde-open (gnome-open in, well, gnome / ubuntu) to use defaults that are used in dolphin / nautilus (stored in ~/.local/share/applications/mime-apps.list I think).

*xdg-open* uses *kfmclient* when called in a KDE session, *gnome-open* when called in Gnome,* exo-open* in XFCE and *run-mailcap* otherwise

---

