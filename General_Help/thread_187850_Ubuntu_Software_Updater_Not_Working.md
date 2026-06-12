---
title: "Ubuntu Software Updater Not Working"
date: 2006-06-03
forum: General Help
---

### Post by Blarion on 2006-06-03
I installed software recently that had a dependancy I could not find. Xlibs to be exact. So i used -force to work around it. Now whenever I launch Ubuntu Software Updater, I get the following message:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

But if I run sudo apt-get install -f, I will lose the software! Please help.

---

### Post by Blarion on 2006-06-04
Can someone please help? This is really bugging me.

---

### Post by xXx 0wn3d xXx on 2006-06-04
[QUOTE=Blarion]I installed software recently that had a dependancy I could not find. Xlibs to be exact. So i used -force to work around it. Now whenever I launch Ubuntu Software Updater, I get the following message:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

But if I run sudo apt-get install -f, I will lose the software! Please help.[/QUOTE]
Run sudo apt-get -f install it will only remove the software that is messed up. You can then re-install it without loosing your config files.

Try installing xlibs this way.
> wget [http://www.artfiles.org/ubuntu.com/a...8.2-77_all.deb](http://www.artfiles.org/ubuntu.com/a...8.2-77_all.deb)
sudo dpkg -i xlibs_6.8.2-77_all.deb 

---

### Post by Blarion on 2006-06-04
But I want to keep the software that is missing the dependancy, because it still works.

---

### Post by Blarion on 2006-06-05
Fixed!

[http://www.ubuntuforums.org/showpost.php?p=947186&postcount=2](http://www.ubuntuforums.org/showpost.php?p=947186&postcount=2)

---

