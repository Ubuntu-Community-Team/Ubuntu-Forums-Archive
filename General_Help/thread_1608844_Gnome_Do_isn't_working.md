---
title: "Gnome Do isn't working"
date: 2010-10-29
forum: General Help
---

### Post by ctult on 2010-10-29
Gnome Do is not opening, an when I open it in the command line it says this:

```

sam@sam-laptop:~$ gnome-do[Error 13:02:20.335]

(Do:3277): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[COLOR=Red]**[Error 13:02:20.335]**[/COLOR] Missing login credentials. Please set login information in plugin configuration.

```

And if I run it at root it works, but doesn't do anything.

Please help.

Thanks in advance,
CTuLT

---

### Post by TeoBigusGeekus on 2010-10-29
> **ctult said:**
> Missing login credentials. Please set login information in plugin configuration.

I think it might be a plugin you've turned on and somehow misfired.
Try to find the folder with the gnome-do settings in your /home partition and delete it. It could be something like .gnome-do or a folder inside your ~/.local folder, I don't know.

---

