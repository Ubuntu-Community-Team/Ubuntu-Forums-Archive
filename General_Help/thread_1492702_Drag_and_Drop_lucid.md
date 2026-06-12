---
title: "Drag and Drop? lucid"
date: 2010-05-25
forum: General Help
---

### Post by fasteddi on 2010-05-25
Hey all...

I was wondering if there is a way to be able to drag and drop files in system folders? I tried and I got a message saying that I do not have permission to do this. I know about sudo but dont want to have to use it every time I wanna move a file or folder into a system folder.

Better explanation... I wanna put new screenlet widgets in the /etc/screenlet folder and when I drag and drop them in it gives that message above. First off... am I doing this correctly or should I be doing this another way. I read a thread about making a drag and drop executable but Im not sure that is what I am looking for.

Thanks all for the help

---

### Post by mc4man on 2010-05-25
> what I am looking for
a root file browser window

Go Alt+F2 
put this in box and click 'run '
```
gksu nautilus
```

As far as your screenlets - /etc/screenlet doesn't appear to be the place or means to adding new ones.

I don't have this screenlets thing installed but if it's the one in the repo I'd do some reading here first

[http://screenlets.org/index.php/FAQ#How_do_I_install_new_Screenlets.3F](http://screenlets.org/index.php/FAQ#How_do_I_install_new_Screenlets.3F)

[http://screenlets.org/index.php/FAQ#Where_do_I_put_individual_screenlets](http://screenlets.org/index.php/FAQ#Where_do_I_put_individual_screenlets)

ect.ect.


You may want to be a bit careful with adding/removing/editing files in the filesystem as root, at the least be sure about what it's doing

---

