---
title: "One Folder Two Users"
date: 2011-07-24
forum: General Help
---

### Post by Arunomi on 2011-07-24
Hi 

Im trying to make a folder that my Wife and i can have 
together.

But my problem is that if i create, move or copy a file in to this
folder my wife cant read and write to it.

I have created the folder in the home dir and added it to a group.

In that group i and my wife is members.

and i setgid so that all file that's copied or ceated in the folder
gets the grupp id.

but how do i make the premissions to set it self to rwx.?

---

### Post by capscrew on 2011-07-24
> **Arunomi said:**
> Hi 

Im trying to make a folder that my Wife and i can have 
together.

But my problem is that if i create, move or copy a file in to this
folder my wife cant read and write to it.

I have created the folder in the home dir and added it to a group.

In that group i and my wife is members.

and i setgid so that all file that's copied or ceated in the folder
gets the grupp id.

but how do i make the premissions to set it self to rwx.?

Set the umask to 002. 

The default umask is 022.  The umask sets the default creation for directories and files like this```

umask = 022 (the Ubuntu default)

directory (raw - umask = default)
=========
raw     = 777
umask   = 022
default = 755 = rwxr-xr-x

file (raw - umask = default)
====
raw     = 666
umask   = 022
default = 644 = rw-r--r--

```

The 002 umask sets files and folders to this```

directory = 775 
file      = 664
```

You can set the umask in the /etc/profile file.  You can use any text  editor you want.  This file is owned by root so you need to use sudo at the terminal or gksudo from nautilus (alt-f2).  At the very bottom of the file add this```
umask 002
```

---

