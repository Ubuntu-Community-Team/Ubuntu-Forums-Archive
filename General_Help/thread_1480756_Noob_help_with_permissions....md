---
title: "Noob help with permissions..."
date: 2010-05-11
forum: General Help
---

### Post by lakedude on 2010-05-11
I needed to edit one line of a text file in /etc/.

Unfortunately the owner of said file was "root" and I was only logged in as a normal user.  

This type of thing does not come up while using Puppy Linux.

I "fixed" this type of issue in Sabayon Linux by making a shortcut to the file manager "as root" so even logged in as a regular user root files could be modified by supplying the root password.

How can I do this in Ubuntu using a GUI?  Seems like I don't have permission to do the things I need to do? 

I did get the line of text modified by going to the console but that was a pain in the neck and now I've messed up the ownership of that file (but is still works fine).

Please help.

TIA!

---

### Post by ubunterooster on 2010-05-11
next time right-click the file. Select "open with">other file. "use a custom command", that command being "gksu gedit"

---

### Post by DavinA on 2010-05-11
Alt-F2 opens a Run Application dialog
From there you can run:
```
gksudo gedit
```
to open the gedit text editor with elevated privledges.

---

### Post by bredman on 2010-05-11
Ubuntu is unusual because there is no actual root user. Instead there is a program for pseudo-root access, known as sudo. This is for safety reasons.

To edit a file as root, open the terminal (use Ctrl-Alt-t or any other method)

Enter the command
sudo gedit <filename>
Enter your password

This will open a graphical editor with root permissions.

When you get used to Ubuntu, you will see that sudo is used for a lot of the configuration work.

---

