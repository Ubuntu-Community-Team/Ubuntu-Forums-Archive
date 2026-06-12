---
title: "linux filesystem"
date: 2010-06-11
forum: General Help
---

### Post by nischalinn on 2010-06-11
I entered in the /etc/. I got a long list of files. But I can't open the files that are **white colored** like _**mtab**_ or etc->X11->**xorg.conf. **

When I do:
[B] /etc/X11$ cd xorg.conf
bash: cd: xorg.conf: Not a directory
[/B]
How can I open such files?

---

### Post by Naggobot on 2010-06-11
By default you can open files located only in your /home/[username]/ folder. All other files and folders are owned either by system or some other user. 

Only reason to edit files located elsewhere in the system is when you for some reason need to manually change your system configuration. This arises only if you have some specific problem you need to solve.

By default there is no reason to edit or open these files and they should not be edited or opened. 

Now if you for some reason need to operate with files owned by the system then the command you need is sudo or gksudo for graphical applications. 

Brown files are folder there fore you can open them with cd command. Other files (white) are either text or binary files and in order to edit with them you need to know what application to use. Generally binary files are not editable by mortals :p. Text files can be edited with gedit. 

If you really need to edit xorg.conf then the command you need to use is

```
gksudo gedit xorg.conf
```

Now if you do not have any reason to edit this file then do not edit it. If you just want to view the file then you can just type

```
gedit xorg.conf
```

which will open the file in view only mode, you can not save changes.

---

### Post by beckols on 2010-06-11
You should probably read up a little on the basics before you post questions like this.  This thread: [http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)

Is a sticky in the Absolute Beginner's Forum, and it contains plenty of good references to get you started.  Also, you can learn some basic shell commands and other misc. goodies from the link in my sig.

---

### Post by Naggobot on 2010-06-11
Now if all of the easy questions are left unanswered then what there is left to answer?

:lolflag:

I personally appreciate easy questions since I can not answer difficult ones and in the process I may learn to answer also the difficult ones. 

See I learned something from this thread too. Thank for both of you for your posts, especially the link was informative.

---

### Post by beckols on 2010-06-11
Haha, I agree it is nice when there is an easy question to answer.

---

