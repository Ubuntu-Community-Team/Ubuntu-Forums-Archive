---
title: "Install eclipse manually"
date: 2010-06-29
forum: General Help
---

### Post by peter27 on 2010-06-29
I have downloaded and unzipped eclipse. 

I would like eclipse to start up when I write "eclipse" in from command prompt. 

Thanks in advance.

---

### Post by dino99 on 2010-06-29
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)
[http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)

---

### Post by forestG on 2010-06-29
> **peter27 said:**
> I have downloaded and unzipped eclipse. 

I would like eclipse to start up when I write "eclipse" in from command prompt. 

Thanks in advance.

Hi!

You could write to the $HOME/.bashrc file the following

alias eclipse=/absolute/path/to/eclipse

you could write this command to /etc/profile file to make the alias available for all users.
One more thing you could do is that you could go the /usr/bin folder and add a shortcut there named eclipse that will point to your eclipse executable file.

Additionally you could add a menu item in the applications menu. If you click on the icon and go to the directory of eclipse you could also use the original icon of eclipse.
Just right click to applications go to programming tab and add a new item.

Anyway try googling linux permanent alias and you will find some very useful links

---

### Post by peter27 on 2010-07-13
Thanks a lot both of you! :D

---

