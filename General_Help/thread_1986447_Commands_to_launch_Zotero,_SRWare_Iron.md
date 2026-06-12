---
title: "Commands to launch Zotero, SRWare Iron?"
date: 2012-05-24
forum: General Help
---

### Post by Bucky Ball on 2012-05-24
Hi all,

I like the OS to be as non-apparent as possible and one way of achieving this is to use shortcut keys for regularly used apps.

I've been hunting but cannot find the commands to launch these two apps:

Zotero standalone
SRWare Iron

If anyone can help me out be much appreciated.

* Typing 'zotero' in to a terminal did launch it once, but oddly enough, never again. :shock:
* I can't find Iron in all the usual places so can't figure what I might try. I've tried the obvious like 'iron' 'srware-iron' etc ...

Tnx in advance ...

---

### Post by phaed on 2012-05-25
There won't be shortcut keys for Zotero by default, unless you installed it from a package that sets that up for you. Did you just unzip the archive somewhere? If so, you need to create your own shortcut in System Settings -> Keyboard -> Shortcuts tab.

Select "Custom shortcuts".

Click the + sign, give it a name like Zotero, and the command would be the path to the Zotero launcher. For example, if you extracted it in your Downloads folder, then the command would be "/home/USER/Downloads/Zotero_linux-x86_64/zotero". Click apply.

Then click on the word "Disabled" and it will change to "new accelerator", and that's when you enter the key combo you want.

---

### Post by Bucky Ball on 2012-05-25
I know how to setup a short cut. The terminal commands to launch these apps is what I'm after.

---

### Post by vasa1 on 2012-05-25
> **Bucky Ball said:**
> I know how to setup a short cut. The terminal commands to launch these apps is what I'm after.

This maybe an indirect way but if you run:
dpkg --get-selections > ~/Desktop/installed-software
You'll get a file called installed-software with a list of programs with their "command names".

---

### Post by Toz on 2012-05-25
> **Bucky Ball said:**
> I know how to setup a short cut. The terminal commands to launch these apps is what I'm after.

Neither of these packages are in the default repositories, so it depends on how you installed them. As @phaed says, you need to figure out where you installed, or more likely uncompressed, the packages and you'll find the executables in there somewhere.

---

### Post by Bucky Ball on 2012-05-25
Yep, hunted down and this seems to launch SRWare Iron:

```
/usr/share/iron/iron
```

... while:

```
/home/binky/zotero/zotero
```

... launches the other. Easiest way to find the execute command is to find the .desktop files of each like so:

```
locate zotero.desktop
```

Do the same for 'iron.desktop'. In there you will find these details, or something similar:

```
[Desktop Entry]
Name=Zotero
Comment=Open-source reference manager (standalone version)
Exec=**/home/binky/zotero/zotero**
Icon=accessories-dictionary
Type=Application
StartupNotify=true
```

With either .desktop file, look for the line beginning with 'Exec='. The part of the line I have in bold is the command to launch the app. Solved. Thanks. ;)

---

