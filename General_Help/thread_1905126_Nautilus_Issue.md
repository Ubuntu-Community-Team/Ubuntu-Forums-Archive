---
title: "Nautilus Issue"
date: 2012-01-06
forum: General Help
---

### Post by ekosUF on 2012-01-06
When using Gnome in Ubuntu 11.10 I was prompted to enter my file manager and accidentally typed Nautilus instead of nautilus and now am getting an error saying Nautilus doesn't exist (notice the capitalization).  I have no issues using nautilus when I use Unity.

Is there a way to fix this problem caused by my silly typo?

Thanks

---

### Post by fragos on 2012-01-06
You didn't tell us what application you were running when that prompt came up so it'd very hard to zero in on where the configuration parameter you need to change is. I will however give you my best guess. Gnome has an Edit Menu function that if I recall correctly is offered as an option when you right click Applications in the upper left panel. Follow the tree down to find a Nautilus or File Manger application. Right click it to edit and one of the fields will be Command. Check there to insure the lower case n.

---

### Post by ekosUF on 2012-01-07
Thanks for the response fragos.  I was prompted to enter the File Manager when I clicked on Places.  If I go to Applications and then click Files (set to run nautilus) I have no problem.  It's only when I try to navigate to a folder such as Home under the Places menu that I have a problem.

Is there a config file which holds info regarding what manager is used when a folder is clicked under the Places menu?

---

### Post by fragos on 2012-01-07
> **ekosUF said:**
> Thanks for the response fragos.  I was prompted to enter the File Manager when I clicked on Places.  If I go to Applications and then click Files (set to run nautilus) I have no problem.  It's only when I try to navigate to a folder such as Home under the Places menu that I have a problem.

Is there a config file which holds info regarding what manager is used when a folder is clicked under the Places menu?

Sounds to me like the Menu Editor might well be your answer. I've not used Gnome since Unity came out with 11.04 so my gnome creds may be out of date as to how to execute the Menu Editor. The command line name for the editor is alacarte. Alt-F2 will bring up a command line without running the terminal.

---

