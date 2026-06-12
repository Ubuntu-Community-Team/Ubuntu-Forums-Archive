---
title: "$HOME variable as shortcut"
date: 2011-03-11
forum: General Help
---

### Post by ~stephan on 2011-03-11
Hello,

I am working on creating an image to be deployed on multiple systems ([http://ubuntuforums.org/showthread.php?t=1678653](http://ubuntuforums.org/showthread.php?t=1678653)).  While everything works great I have one very small issue relating to the shortcuts.

The "master" system has been set up to use Cairo dock with a custom luncher to display the user home directory contents.

So this is essentially referring to /home/user1 on the master system.  While installing on a new system, this shortcut of course refers to /home/user1 while it should be /home/user2.

While it is easy to correct, ideally I would like not to have to edit the shortcut as we will be deploying on about 40 systems.

I tried to use the $HOME variable in the shortcut but that did not work.

Any idea how to use a variable for the $HOME shortcut so it will work on all systems?

Thank you in advance!

---

### Post by dcstar on 2011-03-12
> **~stephan said:**
> 
........
Any idea how to use a variable for the $HOME shortcut so it will work on all systems?


$HOME is a **shell** variable and unless you are using a command shell, it is meaningless to the GUI.

---

### Post by ~stephan on 2011-03-12
Any idea if this is doable with the GUI?

---

### Post by vanadium on 2011-03-12
Perhaps, the gui will work with the symbol ~ (shortcut for /home/$USER)

---

### Post by ~stephan on 2011-03-13
worked prefectly, thanks!

---

