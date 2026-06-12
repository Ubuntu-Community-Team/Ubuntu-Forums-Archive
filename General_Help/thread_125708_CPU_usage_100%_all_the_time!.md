---
title: "CPU usage 100% all the time!"
date: 2006-02-04
forum: General Help
---

### Post by Paool on 2006-02-04
my CPU is still 100% used, even I don't do anything! only KDE, Psi, Akregator and Katapult are turned on...

[http://img461.imageshack.us/my.php?image=zrzutekranu67gx.png](http://img461.imageshack.us/my.php?image=zrzutekranu67gx.png)

What could be problem? Any ideas to fix it?

---

### Post by GeneralZod on 2006-02-04
Run

```

top

```

from the command-line - it will show you all processes, listed by CPU usage.

---

### Post by Paool on 2006-02-04
whiptail uses ~90% - what's that?

---

### Post by GeneralZod on 2006-02-04
[QUOTE=Paool]whiptail uses ~90% - what's that?[/QUOTE]

```

$ apt-cache search whiptail
whiptail - Displays user-friendly dialog boxes from shell scripts

```

Dunno, but it looks pretty badly written :) Must have been installed as a dependency by something.

---

### Post by Paool on 2006-02-04
ok, I've killed it and it's ok now :)

thanks!

---

### Post by az on 2006-02-04
Some tk apps like AMSN use whiptail....

---

