---
title: "Delete notepad"
date: 2010-06-20
forum: General Help
---

### Post by Smika on 2010-06-20
I installed wine and now i get the option to open some files with notepad. I know I can delete this entry when I go to the properties of a document and delete it in the tab "open witth". Is there a way to delete notepad for every file in the system?

Smika

---

### Post by mk1w86 on 2010-06-20
Couldn't you just select something else as the default programme, what problem is having notepad as an option causing? :-s

---

### Post by Smika on 2010-06-20
uhmmm, I am running Linux??? So why I need notepad???

---

### Post by mk1w86 on 2010-06-20
> **Smika said:**
> uhmmm, I am running Linux??? So why I need notepad???

It is part of Wine and is there mainly for test purposes according to this:

[http://wiki.jswindle.com/index.php/Notepad](http://wiki.jswindle.com/index.php/Notepad)

---

### Post by Smika on 2010-06-20
Oke I understand that. Thanks for your help. But why notepad must be integrated in the whole gnome environment?

---

### Post by AMDphreak on 2012-09-29
BUMP.

Quit asking 20 questions about why someone needs this. The point is that it's an unwanted change in GNOME's functionality.

Every time I double click a .sh file, it used to ask me if I wanted to run the script or view the it in gedit. Now, however, it automatically opens it up in Notepad, of all editors. I prefer that my .sh files actually ask me if I want to run them or edit them in gedit.

---

### Post by HiImTye on 2012-09-30
you can clean them from ~/.local/share/applications/mimeapps.list if they exist such as:
```
sed -i 's|notepad.desktop;||g' ~/.local/share/applications/mimeapps.list
```if there are some default associations (in other words, if some still show up in your list), you can use:
```
cat  /usr/share/applications/defaults.list | grep 'notepad.desktop' |  sed 's|notepad.desktop||' >>  ~/.local/share/applications/mimeapps.list
```obviously, this requires that the desktop file be 'notepad.desktop' - cat the list with:
```
cat ~/.local/share/applications/mimeapps.list | grep notepad
```to make sure that it is actually called that, and change the name in the scripts if necessary

also, this is a dead thread, which is against the forum rules, just FYI

---

