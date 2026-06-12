---
title: "Is my Xubuntu 11.04 corrupted?"
date: 2011-06-02
forum: General Help
---

### Post by rewyllys on 2011-06-02
I’ve just installed Xubuntu, on a separate partition in my multi-boot system with a shared /home partition.  Xubuntu seems to me to be behaving strangely, certainly not in ways that seem intuitive to me.  But this is my first experiment with Xfce, so I don't know what is normal and what isn't.

For example:
[INDENT]I open an application.  Most of the time, but not always, its window is locked in the upper left corner of the screen.  I cannot drag any window away from its initial position.  There are no minimize, maximize, and close buttons.  If I have more than one application open, I cannot click in a portion of a window and have the system focus move to that application.  In some of applications, the drop-down menus work properly; but in others, moving the cursor off the top menu item, e.g., File, that opens the drop-down menu makes the drop-down vanish.
[/INDENT]The installation was a clean install, on a reformatted partition, using a CD prepared from the Xubuntu 11.04 64-bit iso.  I've done the install twice, with the same results.

Is the behavior I've described normal?  Or do I have a corrupted installation, possibly from a corrupted iso file?

---

### Post by mike555 on 2011-06-02
Shared /home with what ? if it's not xubuntu no wonder your having troubles , your /home folder has hidden files that help programs run .....

---

### Post by rewyllys on 2011-06-02
> **mike555 said:**
> Shared /home with what ?. . . . 
Shared with Ubuntu 11.04 Classic and LinuxMint 11.

May I take it that the behavior I described IS unusual?

---

### Post by Toz on 2011-06-02
> **rewyllys said:**
> I’ve just installed Xubuntu, on a separate partition in my multi-boot system with a shared /home partition.  Xubuntu seems to me to be behaving strangely, certainly not in ways that seem intuitive to me.  But this is my first experiment with Xfce, so I don't know what is normal and what isn't.

For example:
[INDENT]I open an application.  Most of the time, but not always, its window is locked in the upper left corner of the screen.  I cannot drag any window away from its initial position.  There are no minimize, maximize, and close buttons.  If I have more than one application open, I cannot click in a portion of a window and have the system focus move to that application.  In some of applications, the drop-down menus work properly; but in others, moving the cursor off the top menu item, e.g., File, that opens the drop-down menu makes the drop-down vanish.
[/INDENT]The installation was a clean install, on a reformatted partition, using a CD prepared from the Xubuntu 11.04 64-bit iso.  I've done the install twice, with the same results.

Is the behavior I've described normal?  Or do I have a corrupted installation, possibly from a corrupted iso file?

Sounds like the window manager isn't running. Can you open a terminal window and type in the following:```
ps -ef | grep xfwm | grep -v grep
```
If you get nothing back (just drops to the next line), then type in the following:```
xfwm --replace
```

Does this help?

---

