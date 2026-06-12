---
title: "Undo Configure-debian"
date: 2009-12-02
forum: General Help
---

### Post by kostaben on 2009-12-02
Hi forum,

I was fooling arround with the system and i was curious to see what configure-debian in main menu > system tools is doing. A terminal with a basic graphic environment poped up. There i choosed Gnome. I was expected to be asked for changes but i didnt. The result is a veeeery slow system. Does anyone know what this is, what is it for and the most important how to undo it 8-[](*,)

(sorry for double posting it was in the wrong place before)

---

### Post by utnubuuser on 2009-12-02
hiya -- don't know how to fix your problem, but if I may make a suggestion as to your future "best practices", I'd suggest putting Linux's multi-user architechture to good use.  -- If you're going to mess around with your system, make a new user first, then try your changes on your "new-user's" account.  This way, if you run into a snag, you can simply delete the user. This won't help in all situations, but it can certainly save you some agro.

---

### Post by kostaben on 2009-12-03
Thank you Utnubuuser for the suggestion. I have never thought about it and it seems like a good practice to avoid these errors.

Now after the panic:
"*configure-debian is a program which presents a list of packages which use **Debconf**, Debian's configuration management system.*"

Debconf: "*When packages are being installed, debconf asks the user questions which determine the contents of the system-wide configuration files associated with that package. After package installation, it is possible to go back and change the configuration of a package by using the **dpkg-reconfigure** program*"

dpkg-reconfigure: "*dpkg-reconfigure reconfigures packages after they have already been installed. Pass it the names of a package or packages to reconfigure. It will ask configuration questions, much like when the package was first installed.  *"

So, the bottom line: if you run Debian-configure for a certain package, you should be asked the same questions as the ones when you first install it in regards to the configuration of this package.

Now for my problem: i did not asked any question, and after some restarts the problem went away. Who knows, could be anything, maybe nothing relative with Configure Debian.

Best 

K.

---

