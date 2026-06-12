---
title: "apt-get source baobab is not working"
date: 2010-01-02
forum: General Help
---

### Post by go_beep_yourself on 2010-01-02
I'm using Karmic. I am not sure why this isn't working. I have source code checked off in software repositories, and I see deb-src lines in sources.list. They are not commented. I'd like to recompile the deb and enable "move to trash" from the right click menu.

$ apt-get source baobab 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for baobab

---

### Post by dcstar on 2010-01-02
> **go_beep_yourself said:**
> I'm using Karmic. I am not sure why this isn't working. I have source code checked off in software repositories, and I see deb-src lines in sources.list. They are not commented. I'd like to recompile the deb and enable "move to trash" from the right click menu.

$ apt-get source baobab 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for baobab

It is not a separate package, it is part of the gnome-utils package.

---

