---
title: "Where is the program i downloaded?"
date: 2010-01-03
forum: General Help
---

### Post by JoeyF on 2010-01-03
I downloaded the DEB of Panda3D, It installed. But i don't see it in my applications menu.

I went to search for files and found a bunch of folders  but i can't find the executable to launch it.

And when i do find it how can i add a shortcut to the menu?

Thanks.

---

### Post by lovinglinux on 2010-01-03
Try to reboot. Some applications menu only appears after doing this.

You can find it with this command:

```
whereis packagename
```

Assuming that Panda3D executable is panda3d, then the command would be:

```
whereis panda3d
```

Keep in mind that in Linux, files don't need to have an extension to be executables.

To add a new launcher to the menu go to "System >> Preferences >> Main Menu"

---

### Post by JoeyF on 2010-01-03
I got
```

panda3d: /usr/lib/panda3d /usr/include/panda3d /usr/share/panda3d
```


How do i know which one?

Thanks

---

### Post by MichealH on 2010-01-03
It looks that it is installed as above the person said Try Rebooting or it may be a terminal app and doesn't have a GUI.

---

### Post by Leppie on 2010-01-03
> **JoeyF said:**
> I got
```

panda3d: /usr/lib/panda3d /usr/include/panda3d /usr/share/panda3d
```


How do i know which one?

Thanks

to locate an executable:
```
$which <executable>
```
in your case:
```
$which panda3d
```

---

### Post by lovinglinux on 2010-01-03
EDIT: see post above.

---

### Post by 3rdalbum on 2010-01-03
There's a screencast in my signature that covers this common problem. But from what you describe, it looks like you have only installed data files and not the main program. There may have been two packages that you had to install?

---

### Post by lovinglinux on 2010-01-03
> **3rdalbum said:**
>  But from what you describe, it looks like you have only installed data files and not the main program.

The OP installed a DEB file.

---

### Post by pro-rsoft on 2010-01-05
Panda3D is a library, not a standalone program. Although it does come with helpful tools, usage of Panda3D usually consists of writing a Python program that controls the Panda3D modules, or a C++ program that links to the Panda3D libraries.

The package name does imply that it is a standalone program - this unfortunate naming will be resolved in a future release of Panda3D.

---

