---
title: "Just Installed 9.04. Cannot create/delete folders etc in file manager!Only from shell"
date: 2009-08-13
forum: General Help
---

### Post by psilofox on 2009-08-13
Hello please help,

I'm new to Ubuntu, it's very nice but my god it dictates how it wants you to use it!

I am within the file manager, trying to copy a folder from my desktop to another location but no it just doesn't let me. I can do it all from a shell screen as root but, I cannot even login to X to be able to just copy and paste and do things the way I wanna do them. I feel the security to usability factor is a nuisance for me.

Can someone help me try to achieve what I mentioned. Like trying to right click and copy, pasta, delete create etc in any folder. I have searched google for ages and its doing my nut in! 

Many many many many thanks in advance! . cheers.
grr

---

### Post by michy99 on 2009-08-13
Where are you trying to move the files to? If it is a system folder, you have to have root privileges. To open a file manager with root privileges, enter this in a terminal:```
gksudo nautilus
```However, it is not a good idea to run as root all the time. Do what you have to do and close the window,

---

### Post by martinbaselier on 2009-08-13
Where do you want to copy files to? If the files/directories are owned by root, only root can write to them, with the normal settings.

---

### Post by tgeer43 on 2009-08-13
Yeah, it sure sounds like you're trying to copy to a folder that you don't have the necessary permissions for. This is not a bad thing, If all users were allowed to read/write/execute anywhere they wished there would not be enough forums in the world to solve all of the problems this would create.

If you want to be able to temporarily access things with root privileges but are more comfortable with the nautilus file manager than the command line, you can easily add an "open as administrator" option to the right-click context menu. Just take a look here for simple instructions:

[http://www.watchingthenet.com/ubuntu-tips-for-windows-users-add-open-as-administrator-to-nautilus-right-click-menu.html](http://www.watchingthenet.com/ubuntu-tips-for-windows-users-add-open-as-administrator-to-nautilus-right-click-menu.html)

Just don't go crazy with it or you ***will ***end up with more problems than you care to think about.

tgeer

---

### Post by psilofox on 2009-08-14
Thanks so much for all your help folk :)
Have a nice day/evening!

---

