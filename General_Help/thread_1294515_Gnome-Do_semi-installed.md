---
title: "Gnome-Do semi-installed"
date: 2009-10-18
forum: General Help
---

### Post by beak02 on 2009-10-18
Hi,

I was trying to reinstall gnome do where I ran into problems.  I've done everything I can think to uninstall and then reinstall but Do still seems to be on here - sortof.  I can't use it but running "gnome-do" in a terminal returns the following:
```

lbarnes@lbarnes-laptop:~$ gnome-do
Cannot open assembly '/usr/local/lib/gnome-do/Do.exe': No such file or directory.
lbarnes@lbarnes-laptop:~$
```

I'm slightly confused at the presence of an "exe" but even more that I have been through "completely remove" through synaptic and it's still there!

Help please :)

Luke

---

### Post by beak02 on 2009-10-18
Anyone?

---

### Post by cariboo on 2009-10-18
I recently had the same problem, I removed all traces of Gnome-do from my home directory, then restarted Gnome-do and it worked as it should. Look in ~/.gconf/apps and ~/.local/share for the Gnome-do files.

To view them in nautilus open Places-->Home Folder and press Ctrl-h

---

### Post by beak02 on 2009-10-18
Brilliant!

That worked - I removed all traces of "gnome-do" and re-installed.

Thanks once again!

---

