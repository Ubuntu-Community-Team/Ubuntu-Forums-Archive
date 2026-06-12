---
title: "How to sudo cp?"
date: 2011-05-20
forum: General Help
---

### Post by .psd on 2011-05-20
How to move the file 'gedit' (a .desktop file called 'Text Editor.desktop) from Desktop to usr/share/applications?

ngrlvr@ngrlvr-EX58-UD3R:~$ sudo cp /home/ngrlvr/Desktop/gedit.desktop /usr/share/applications/
cp: cannot stat `/home/ngrlvr/Desktop/gedit.desktop': No such file or directory

---

### Post by mcduck on 2011-05-20
the command syntax is right, but either your path or the file name isn't.

Actually, you said that the file is called "Text Editor.desktop", while in your command you are trying to copy a file called "gedit.desktop". Check which one is right and use that in your command.

---

### Post by .psd on 2011-05-20
That's where I'm lost. On my monitor, on/in Desktop, under the icon it says "gedit". But if I try to drag it to a restricted area it says cannot move "Text Editor.desktop".

So am I trying to copy "gedit", "gedit.desktop", or "Text Editor.desktop"?

It won't let me copy "Text Editor.desktop" because it thinks that's 2 files "Text" and "Editor.desktop".

---

### Post by mcduck on 2011-05-20
That's because your graphical file manager is actually reading the .desktop file and displays name, icon etc. based on what the file describes (that's the very purpose of .desktop files).

Check the correct file name in a terminal with the *ls* command if you are not sure.

Also remember to use quotes with file names that have spaces in them, or escape the space with a backslash.

```
"Text Editor.desktop"
```
or
```
Text\ Editor.desktop
```

---

### Post by .psd on 2011-05-20
Right on the money mcduck! I learned about ls right before I read your post, and decided to remake the file without a space in it (because I hadn't read your post yet). Then I was able to move it :)

Thank you!

---

