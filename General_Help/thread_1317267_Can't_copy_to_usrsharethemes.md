---
title: "Can't copy to /usr/share/themes"
date: 2009-11-06
forum: General Help
---

### Post by Uncle Spellbinder on 2009-11-06
Themes I'd like to copy  or move to ***/usr/share/themes*** doesn't seem possible. I've not had this issue prior to my clean install of 9.10.

```
error moving file: permission denied
```


This happens on any theme I try to move. Ideas?

---

### Post by vancouverite on 2009-11-06
What command are you using?

---

### Post by alphaniner on 2009-11-06
Did you check the permissions on the themes folder?  On my install of 9.10, only root has write access.  Same on my 9.04.  Maybe you changed on your previous install and forgot.

---

### Post by Uncle Spellbinder on 2009-11-06
I'm not using a command. I'm right-clicking and copying to the folder. It's worked prior to 9.10 without issue.

As far as changing permissions, seems everything is grayed out:

[IMG]http://i34.tinypic.com/35hh54l.jpg[/IMG]

---

### Post by pastalavista on 2009-11-06
> **Uncle Spellbinder said:**
> I'm not using a command. I'm right-clicking and copying to the folder. It's worked prior to 9.10 without issue.

As far as changing permissions, seems everything is grayed out:

Run ```
gksu nautilus
``` and navigate to the directory. Right-click and select properties. Then open the permissions tab.

---

### Post by coffeecat on 2009-11-06
> **pastalavista said:**
> Run ```
gksu nautilus
``` and navigate to the directory. Right-click and select properties. Then open the permissions tab.

Oh no! #-o**Never** change the permissions on a root-owned system folder. It's root owned for a reason.

> **Uncle Spellbinder said:**
> It's worked prior to 9.10 without issue.

/usr/share/themes is **always** owned by root, so you cannot have been able to copy into it with the GUI **unless** you opened a file browser with root powers as pastalavista is suggesting. **Don't** change the permissions of the folder, but if you open a file browser with "gksudo nautilus" you'll be able to copy themes into that folder just fine.

However, your screenshot looks like a bit like KDE. If so, use "kdesu konqueror".

---

### Post by SuperSonic4 on 2009-11-06
> **coffeecat said:**
> Oh no! #-o**Never** change the permissions on a root-owned system folder. It's root owned for a reason.



/usr/share/themes is **always** owned by root, so you cannot have been able to copy into it with the GUI **unless** you opened a file browser with root powers as pastalavista is suggesting. **Don't** change the permissions of the folder, but if you open a file browser with "gksudo nautilus" you'll be able to copy themes into that folder just fine.

However, your screenshot looks like a bit like KDE. If so, use "kdesu konqueror".

I suggest using dolphin as it's more user friendly as a file manager than konqueror ```
kdesu dolphin
```

Easier yet is to use the *cp* (copy) or *mv* (move) option from the command line

```
sudo cp -Rv ~/theme_folder /usr/share/themes
``` or ```
sudo mv -v ~/theme_folder /usr/share/themes
```

-v is verbose so it shows what's going on
-R is recursive so it goes into the folder (mv just moves automatically)
sudo gives temporary root access

---

### Post by vancouverite on 2009-11-06
I think that it's worth noting that running nautilus in root mode (which is basically what gksu does) is considered sort of hazardous.

While this is the normal way to move things to places other than your home folder (strange that you could do it before), I wouldn't make a habit of using it this way unless you have a specific task you are performing.

Van

---

### Post by coffeecat on 2009-11-06
> **SuperSonic4 said:**
> I suggest using dolphin as it's more user friendly as a file manager than konqueror

Thanks! I couldn't for the life of me remember the name of the new KDE4 file manager. A bit out of date here. Confirmed gnome man, you see. :wink:

---

### Post by sisco311 on 2009-11-06
If it's a single user system (or you don't want to share the theme(s) with other users) just move the theme(s) in the ~/.themes directory. ~/.themes is a hidden directory in your home directory, you may have to press Ctrl+H to list it. If it's not present, then create it.

---

