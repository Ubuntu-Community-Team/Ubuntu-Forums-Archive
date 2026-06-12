---
title: "automating terminal commands"
date: 2010-01-15
forum: General Help
---

### Post by juzzy on 2010-01-15
Hi
I remember that once upon a time I had automated some tedious commands in the terminal by writing them in a text file and placing an icon on the panel. By clicking the icon the commands ran in the terminal automatically.  I cant for the life of me remember the icon command I used to get this to work.  Can anyone help?
thanks in advance

---

### Post by DGortze380 on 2010-01-15
> **juzzy said:**
> Hi
I remember that once upon a time I had automated some tedious commands in the terminal by writing them in a text file and placing an icon on the panel. By clicking the icon the commands ran in the terminal automatically.  I cant for the life of me remember the icon command I used to get this to work.  Can anyone help?
thanks in advance

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[http://drbrainiac.wordpress.com/2007/11/04/how-to-create-custom-desktop-launchers-in-ubuntu-gnome/](http://drbrainiac.wordpress.com/2007/11/04/how-to-create-custom-desktop-launchers-in-ubuntu-gnome/)

---

### Post by iponeverything on 2010-01-15
If its just a series of commands that you don't have to interact with, it is as simple as putting the commands into a file on your desktop and right-clicking on icon going to properties and clicking the box for execution. And, of course, actual bash scripting is very versatile.. 

If you want to automate something that requires interaction with a shell, something like expect is ideal. 

get it with:

```
sudo apt-get install expect
```

---

### Post by juzzy on 2010-01-26
thanks guys i figured it out!!!!

---

