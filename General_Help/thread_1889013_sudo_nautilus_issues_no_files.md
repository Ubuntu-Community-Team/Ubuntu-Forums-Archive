---
title: "sudo nautilus issues: no files"
date: 2011-11-30
forum: General Help
---

### Post by strange_cathect on 2011-11-30
I'm trying to move some gnome shell theme files from my desktop and /home folder into user/shared/ directory.

Permission is denied so I thought I'd become root and open nautilus. When I do so, nautilus opens however it will not display any files on my desktop, even if I select to show hidden files. 

When I try to gksudo or sudo nautilus, terminal gives the following errors:

> (gksu:2809): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2809): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2809): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2809): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
** (nautilus:2811): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension

--- Hash table keys for warning below:
--> l2066
--> root
--> inode/directory

--- Hash table keys for warning below:
--> file:///
--> file:///root
Shutting down nautilus-gdu extension

(nautilus:2811): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)


What gives?

---

### Post by jjex22 on 2011-11-30
Hi there, did you switch user to root? (su root) that would display the root user's home folder.

you need to open nautilus with root privilages - press alt+F2 and type in 

gksudo nautilus

This means you're the same user, so you should see your home folder, hope it helps :)

---

### Post by deonis on 2011-11-30
try to use mc instead of nautilus apt-get install mc. But you shouldn't have any problem using "sudo nautilus" in terminal

---

### Post by strange_cathect on 2011-11-30
Thanks for the reply. I haven't switched user to root. When I gksudo or sudo nautilus, it opens, but it appears like there are no files on the desktop. See attached image.

---

### Post by strange_cathect on 2011-11-30
Wait, I'm an idiot. I was looking at root's desktop. Thanks for the hand, folks.

---

### Post by jjex22 on 2011-11-30
If Alt+F2 didn't work, drs305 solved his pixmap issues with this package:

> **drs305 said:**
> 
```
sudo apt-get install gtk2-engines-pixbuf
```

hope it works for you too! :)

---

### Post by mcduck on 2011-11-30
> **strange_cathect said:**
> Thanks for the reply. I haven't switched user to root. When I gksudo or sudo nautilus, it opens, but it appears like there are no files on the desktop. See attached image.

That's because you are running Nautilus as root. You are viewing root's desktop, not your normal user's.

Just browse to /home/yourusername/Desktop to access your normal user account's desktop directory.

---

### Post by jjex22 on 2011-11-30
> **deonis said:**
>  But you shouldn't have any problem using "sudo nautilus" in terminal

It's best to get in the habit of using

```
 gksudo
```

or

```
 kdesudo
```

for graphical programs instead of just sudo as it can on occasion cause problems :)

---

