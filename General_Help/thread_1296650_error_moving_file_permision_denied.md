---
title: "error moving file permision denied"
date: 2009-10-20
forum: General Help
---

### Post by justincrediblee on 2009-10-20
Cant move files or look at directory .... there is one account on this computer and its logged in plz help.....

---

### Post by 3rdalbum on 2009-10-20
What files are you trying to move, and what directories are you trying to look at? Remember, you can't modify files outside your home directory unless you become root through the "[sudo]("https://help.ubuntu.com/community/RootSudo")" command

---

### Post by justincrediblee on 2009-10-20
Im trying to move the fire fox from favorites to desktop lol and im trying to look at  You do not have the permissions necessary to view the contents of "root" its like im  not the administrater but i have to be theres only one account and im on it

---

### Post by mcduck on 2009-10-21
> **justincrediblee said:**
> Im trying to move the fire fox from favorites to desktop lol and im trying to look at  You do not have the permissions necessary to view the contents of "root" its like im  not the administrater but i have to be theres only one account and im on it

The "Favourites" is not an actual location, what you see there are just links to files that are actually located elsewhere. And you can't move Firefox itself. It's installed for the whole system and it's files don't belong to your user. (Besides, moving the actual program would break it anyway).

If you want a desktop launcher for Firefox, then go to the Applications-menu and right-click Firefox in there & select "Add this launcher to desktop". You can also just drag&drop things from the menu into desktop and panels to automatically make launchers for them.

---

### Post by 3rdalbum on 2009-10-21
> **justincrediblee said:**
> Im trying to move the fire fox from favorites to desktop lol and im trying to look at  You do not have the permissions necessary to view the contents of "root" its like im  not the administrater but i have to be theres only one account and im on it

I'm still not really sure exactly what you're trying to move, sorry. Can you please post the file path of the file that you are trying to move, and why you are trying this?

But there are two accounts on your Linux system that you need to be aware of: Your user account, and root.

Your user account can **only** modify files that are inside your home directory; this is for security and reliability purposes. If you want to modify **anything** outside your home directory, you need to temporarily become root.

Try opening a file browser as root by using this command (hit Alt-F2 and then type the command):

```
gksudo nautilus
```

If you want to move files that are outside your home directory, then use this window to move them. But be careful - the file browser is running as root, so it's now possible to mess up your system by moving or modifying the wrong thing.

For more information on becoming root, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

