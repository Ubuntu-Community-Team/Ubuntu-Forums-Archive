---
title: "change security access"
date: 2011-08-25
forum: General Help
---

### Post by moijdikssekool on 2011-08-25
hello
i use eclipse through the application/programming menu but i have some security problems when i compile
i have looked for eclipse icone, i have found one, in /usr/lib/eclipse and (right click, properties, pemissions) changed the security access (write and read) but the problem is still there if i launch eclipse through the application menu
How to change definitively the security acces?
PS: i have to launch eclipse in a terminal: sudo eclipse to have no security problem

---

### Post by fdrake on 2011-08-25
> **moijdikssekool said:**
> hello
i use eclipse through the application/programming menu but i have some security problems when i compile
i have looked for eclipse icone, i have found one, in /usr/lib/eclipse and (right click, properties, pemissions) changed the security access (write and read) but the problem is still there if i launch eclipse through the application menu
How to change definitively the security acces?
PS: i have to launch eclipse in a terminal: sudo eclipse to have no security problem

actually the write aand read permission you changed if for the users to write ned read the /usr/lib/eclipse file. 

if you compile and want to change the script of system file than you need to use sudo. the only way to make eclipse change the source of system files without sudo is by applying a suid sticky bit. That would compromise you whole system because anyone having access of eclispe will have the power to change all your system files. (so don't do it!)

---

