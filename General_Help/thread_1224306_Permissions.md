---
title: "Permissions"
date: 2009-07-27
forum: General Help
---

### Post by SteveB357 on 2009-07-27
I have a continuing problem with permission to modify, read/write, or otherwise access certain files, or to change who has permission to do what.

Currently, my system has decided that I don't have permission to write to my usb thumb drives.  There are a few other files on the desktop that suddenly have this problem as well.

I say suddenly, because all of these things started after moving to Jaunty.

I can't change any of these either.

When I right click on the files, or drives, and go to properties, permissions, and try to change them, I'm told I don't have permission to make these changes.

This is a desktop installation.  I am the owner of the machine.  I am the only user.

How can I overcome these things?

---

### Post by wojox on 2009-07-27
Open your terminal and use sudo to change permissions.

---

### Post by HNP45acp on 2009-07-27
[FONT=Times New Roman][SIZE=3]Hi Steve[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I feel your pain. I’m a newbie (~1 year) and still have problems with PERMISSIONS. I often create/move/delete anything from files to whole partitions because I’m leaning disk partitioning and virtual machines.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Using the terminal is too slow for me and although tools like Eiciel that are suppose to make things easier through the use of a GUI, they do not work =/. Eiciel seems to also create a new set of problems – we then need to set everything to ACL permissions.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I hope that someone will work on an [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]1)[/SIZE] [SIZE=3]An easy to use graphic interface application for PERMISSIONS. The Advanced File Permissions utility in Nautilus is easy to enable and use, but I don’t think you can apply permissions in a Recursive manner. It is somewhat limited, and it doesn’t always let me do whatever I want even when I’m root (ALT+F2 > gksudo Nautilus).[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2)[/SIZE] [SIZE=3]An easy to use graphic interface application for editing FSTAB file. I have recently ruined something and I think I might have done it while editing the fstab file. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]So you might be stuck with using the terminal for now. This isn’t bad if you don’t change things around too often. Check these pages: [/SIZE][/FONT]
 
[[FONT=Times New Roman][SIZE=3][COLOR=#800080]https://help.ubuntu.com/community/FilePermissions[/COLOR][/SIZE][/FONT]]("https://help.ubuntu.com/community/FilePermissions")
 
[[FONT=Times New Roman][SIZE=3][COLOR=#800080]http://psychocats.net/ubuntu/permissions[/COLOR][/SIZE][/FONT]]("http://psychocats.net/ubuntu/permissions")
 
[FONT=Times New Roman][SIZE=3]I really look forward to see what more experience Ubunters have to say. Look forward to learn more about the subject.[/SIZE][/FONT]

---

