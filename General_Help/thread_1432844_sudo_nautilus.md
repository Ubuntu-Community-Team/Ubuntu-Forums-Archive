---
title: "sudo nautilus"
date: 2010-03-18
forum: General Help
---

### Post by Alex Farber on 2010-03-18
To execute some task with root rights, I type this in the terminal window:
sudo nautilus

It works as needed, but terminal window remains opened. Is there some way to run nautilus with root rights, without this terminal window?

BTW, sometimes is opens Nautilus without asking the password, and I have root rights. Looks like Ubuntu bug?

---

### Post by beastrace91 on 2010-03-18
> **Alex Farber said:**
> BTW, sometimes is opens Nautilus without asking the password, and I have root rights. Looks like Ubuntu bug?

Ubuntu holds your root password in an open terminal for 10(?) mins after you enter it. Meaning once it is entered you don't have to enter it again for awhile to run further super user commands. Ubuntu considers this more of a "feature" than a "bug"

As for running a root nautilus with out having a terminal, press alt+f2 and run **gksudo nautilus** it will prompt you for your password and then open the root file viewer.

Regards,
~Jeff

---

### Post by MelDJ on 2010-03-18
the second thing might be because you have used sudo in the last 15 minutes. 9.10 comes with this feature where you dont need to type the password if you have used sudo in the last 15 minutes

---

### Post by -grubby on 2010-03-18
It's simple - press Alt+F2, and then type "gksudo nautilus". On that note, for GUI applications, running them with sudo is incorrect - use gksudo (or ksu on KDE.) And that's not a bug, there's a thing called "sudo timeout" - if you use a command with sudo, for the next 15 minutes you don't need to use your password with sudo.

---

### Post by philinux on 2010-03-18
The guys above are right to say use gksudo. The reasons are spelled out here.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Alex Farber on 2010-03-18
Thank you, Alt+F2 and gksudo did the trick.

---

