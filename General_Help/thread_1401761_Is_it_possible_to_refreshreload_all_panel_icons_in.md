---
title: "Is it possible to refresh/reload all panel icons in Gnome?"
date: 2010-02-08
forum: General Help
---

### Post by Rytron on 2010-02-08
Hi.
Is it possible to refresh/reload all panel icons in Gnome? Is there a command / GUI method?
Thank you.

---

### Post by drs305 on 2010-02-08
It depends on what exactly you want to do.  

You can refresh the panel with
```
killall gnome-panel &
```

If you want to return the panel to the default settings:
```

gconftool-2 --recursive-unset /apps/panel && killall gnome-panel &

```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Rytron on 2010-02-08
Hi drs305. Much appreciated. ;)

---

### Post by karthick87 on 2010-11-28
What does the ampersand ([SIZE=4][COLOR=Red]&[/COLOR][/SIZE])mean?

---

### Post by drs305 on 2010-11-28
> **karthick87 said:**
> What does the ampersand ([SIZE=4][COLOR=Red]&[/COLOR][/SIZE])mean?

The & added to the end of a command in terminal allows you to continue to use the terminal for other commands. If not added, the terminal remains 'bound' to the original command and cannot be used for anything else until that process is complete.

For example, if I run "gedit myfile" in terminal, gedit will open but I cannot use the terminal for anything else until I close gedit. If I use "gedit myfile &" gedit will open but I can return to the terminal and use it for other commands.

Of course, you can always open a new terminal instead, and now you can also open a new tab in the same terminal window even without the "&". I just find it easier to add a "&" on the keyboard than opening another terminal if I need to run more commands in a sequence.

---

### Post by karthick87 on 2010-11-28
@drs305 Thank you :)

---

