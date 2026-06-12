---
title: "How to create desktop shortcuts for folders (through file manager)?"
date: 2012-03-06
forum: General Help
---

### Post by NonStop on 2012-03-06
I have 11.10, and I know how to create desktop shortcuts for programs (righ-clicking on item through start menu). 

However, how do I create shortcuts for folders? For example, it would be nice to have a shortcut to my documents folder on my desktop. If I highlight a folder from file manager and move it to the desktop, it doesn't create a shortcut, but instead moves the folder and all its contents over.

Any way to fix this? And this should be made easier for the future I reckon.

Thanks in advance ):P

---

### Post by lindsay7 on 2012-03-06
right click on the folder and then click on "make Link"  you can then move this to where you want it.

---

### Post by ankspo71 on 2012-03-06
Hi,
If you are using pcmanfm as your file manager, then there is no way to do this through the file manager. But the good news is there is a tool installed in Lubuntu that lets us create desktop shortcuts (called lxshortcut).

Since you would like to create shortcuts on your desktop, open your terminal and change directories to the desktop with this command:

```
cd Desktop
```

Now, use this command to instruct lxshortcut to create a shortcut named documents.desktop

```
lxshortcut -o documents.desktop
```

Then you can enter the following details:
Name = Documents
Command= pcmanfm Documents
Icon= You will probably want to look for an icon in: /usr/share/icons/elementary/places/48 (for example)

By the way, all *.desktop files are shortcuts (aka application launchers). The file extension name and where you are saving them to is a coincidence.

---

### Post by NonStop on 2012-03-07
Thank you for the responses, the first one doesn't work, the second one does, thank you, although its a heck of a long-winded approach, something that I think the lubuntu team should work on.

---

### Post by alan2442 on 2012-06-04
Hi all
newbie here, was looking for the same answer myself and by trial and error found out that Thunar file manager has the command as in MS Explorer.
Useing Lubuntu Precise

---

### Post by tonycabo on 2012-12-17
Hola,

This thread is some months old now, but I've got an answer that fits more accurately the original question.

In pcmanfm it is possible to create desktop shortcuts to anything with GUI. You just have to right click on the desktop > Create New... > Shortcut. You get a window where you type the name of the .desktop file, without the .desktop extension, and right after you jump to a second window where you can set an icon through GUI file manager, the actual name that the shortcut will be displaying and finally, the command ([FONT=Courier New]pcmanfm Documents[/FONT] in this case).

It's the same process described by ankspo71 but with GUI. Thank you!

;D

---

