---
title: "Misc questions"
date: 2006-02-16
forum: General Help
---

### Post by Mishal on 2006-02-16
1) Sometimes Ubuntu exits from GNOME and takes me to the terminal and asks for username and password. But once I enter the info, the terminal logs in to the account but does not open GNOME. How do I enter GNOME? What is the code?

2) How do I make shortcuts to folders (not partitions)? Whichever way I change the permissions, I am always denied the permission to make a shortcut to any folder.

---

### Post by gibson on 2006-02-16
Exits from gnome?

You may have inadvertantly switched to a tty. If this is the case CTRL-ALT-F7 will take you back to gui.

If gdm has died/crashed... type  

> sudo /etc/init.d/gdm restart.

"shortcuts" in linux are called symbolic links to directories (folder is a winslows term)

to make one, here is an example of how i mount my music from my windows partition

> ln -s /media/hda5/Desktop/Music/ /home/gibson/music

then you can use the chmod command to set the rights


hope this helps
gb

---

### Post by Mishal on 2006-02-16
Thanks a lot :)

---

### Post by Mishal on 2006-02-16
More questions:
3) How do I make those symbolic links without using commands?
4) How do I delete these symbolic links? Even if set the permissions to 777, I cannot delete it!
5) How do I expand the capacity of the GNOME-panel drawer from holding 2 objects to holding unlimited objects?
6) How do I hide files?

---

### Post by yota on 2006-02-16
Hi,

3) In gnome you can create links by drag&dropping with the third mouse button

4)Uhm... if "folder_link" is a link pointing to a directory you have to remove "folder_link" and NOT "folder_link/", so "rm folder_link" should work...

6) Files with names starting with a dot (like .file for instance) are hidden

---

### Post by Mishal on 2006-02-16
If I rename Windows system folders like 'Recycled' and 'System Volume Information' to make them hidden, will Windows be having problems working?

---

### Post by LordBug on 2006-02-16
If you mean re-naming them to ".Recycled" and ".System Volume Information", then the answer is yes, Windows will get fussy.

---

### Post by Mishal on 2006-02-18
7 ) Does dpkg solve dependency problems?
8 ) Does anyone use GQView here? If yes, any idea what to do when the 'Set as Wallpaper' does not work?
9 ) To those who has nVidia cards, where do I get NV-Control X extension and how do I install it?

---

### Post by Bou on 2006-02-18
[QUOTE=LordBug]If you mean re-naming them to ".Recycled" and ".System Volume Information", then the answer is yes, Windows will get fussy.[/QUOTE]

However, you can create a text file called .hidden and place it on your home folder, then open it and copy the names of the directories you want to hide

> Recycled
System Volume Information

That way they won't be displayed.

---

### Post by Mishal on 2006-02-18
Thanks a lot :)

---

### Post by Mishal on 2006-02-18
Bump
> 
7 ) Does dpkg solve dependency problems?
8 ) Does anyone use GQView here? If yes, any idea what to do when the 'Set as Wallpaper' does not work?
9 ) To those who has nVidia cards, where do I get NV-Control X extension and how do I install it?

---

