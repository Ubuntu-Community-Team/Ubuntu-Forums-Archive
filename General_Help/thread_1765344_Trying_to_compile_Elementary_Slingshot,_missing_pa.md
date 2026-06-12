---
title: "Trying to compile Elementary Slingshot, missing package gee-1.0?"
date: 2011-05-23
forum: General Help
---

### Post by hitchhiker4242 on 2011-05-23
I was trying to install Slingshot by the Elementary Team as per the instructions here: [http://adityaiitj.wordpress.com/2011/04/19/try-something-new-beautiful-ubuntu-part2slingshot/]("http://adityaiitj.wordpress.com/2011/04/19/try-something-new-beautiful-ubuntu-part2slingshot/"). When I run ./build_run, I keep getting the following error:

```
error: Package `gee-1.0' not found in specified Vala API directories or GObject-Introspection GIR directories
Compilation failed: 1 error(s), 0 warning(s)
mv: cannot stat `slingshot': No such file or directory
slingshot: no process found
```

Can anyone help?

---

### Post by mc4man on 2011-05-23
what are you using natty, maverick or other?
(just built on natty no problem, if on maverick you'd need to add the ppa as mentioned.
As far as libgee - the natty version worked fine, looks like ppa has an updated one for maverick
Either way make sure libgee-dev is installed

(As far as natty, may be okay on classic, while it will run/work in unity login doesn't seem suitable

Actually does work ok in the unity login - judt not too suitable for running from the  unity launcher, but works fine from a launcher on desktop or in a folder

---

### Post by hitchhiker4242 on 2011-05-23
Right, sorry forgot to mention that. I'm on Maverick. I'm not exactly sure what ppa you're referring too. If you mean the Vala one then I've already done that. I installed libgee-dev, but now I get the following output:

```
/home/michael/experimental/slingshot.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/widgets/AppItem.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/widgets/CompositedWindow.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/widgets/Grid.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/widgets/Indicators.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/widgets/PageItem.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/widgets/PageList.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/widgets/Searchbar.vala.c:7: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/frontend/Utilities.vala.c:28: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
/home/michael/experimental/backend/GMenuEntries.vala.c:8: fatal error: gnome-menus/gmenu-tree.h: No such file or directory
compilation terminated.
error: cc exited with status 256
Compilation failed: 1 error(s), 0 warning(s)
mv: cannot stat `slingshot': No such file or directory
slingshot: no process found

```

---

### Post by mc4man on 2011-05-23
Your missing some build deps, how many don't know - run this and try again
```
sudo apt-get install build-essential libgtk2.0-dev libgnome-menu-dev
```

---

### Post by hitchhiker4242 on 2011-05-23
After following your instructions there were still a couple of things missing, but I went ahead and tried installing libwnck-dev and libunique-dev and all that did the trick. Thanks for your help!

---

