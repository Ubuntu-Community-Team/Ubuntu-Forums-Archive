---
title: "Can't open update manager"
date: 2011-02-24
forum: General Help
---

### Post by squashnuts on 2011-02-24
Hello, I just installed Ubuntu 10.10 on my new computer, and I've experienced some problems. I can't open Update Manager, when I try to open it, it says: Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'usage:' is not known on line 54 in source list /etc/apt/sources.list'

Is there any way to fix this problem?
I also can't open Ubuntu Software Center.

Please help.

---

### Post by plucky on 2011-02-24
> **squashnuts said:**
> Hello, I just installed Ubuntu 10.10 on my new computer, and I've experienced some problems. I can't open Update Manager, when I try to open it, it says: Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'usage:' is not known on line 54 in source list /etc/apt/sources.list'

Is there any way to fix this problem?
I also can't open Ubuntu Software Center.

Please help.

Welcome to the Forum,

Open a terminal and post output of ```
cat /etc/apt/sources.list
```

To edit the file sources.list use ```
gksudo gedit /etc/apt/sources.list
```

The error is in line 54.

---

### Post by squashnuts on 2011-02-24
I fixed it.... I just had to put a # infront of the line that had the error... THANKS

---

### Post by squashnuts on 2011-02-24
And actually Ive been using ubuntu for over a year now but i just bought a new computer so i wanted to install it

---

