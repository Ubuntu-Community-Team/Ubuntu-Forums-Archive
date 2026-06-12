---
title: "How to enable core dump"
date: 2010-05-27
forum: General Help
---

### Post by Alex Farber on 2010-05-27
To get core dump from my program, I execute the following commands from the terminal:

ulimit -c unlimited
myprogram

After program crash, I see core file in the home directory. How can I make this mode persistent, to have code dump always?

---

### Post by rnerwein on 2010-05-27
> **Alex Farber said:**
> To get core dump from my program, I execute the following commands from the terminal:

ulimit -c unlimited
myprogram

After program crash, I see core file in the home directory. How can I make this mode persistent, to have code dump always?

hi
you can find the file limits.conf in /etc/security
as super user you can edit this file ( at end of the file insert )

your_username    soft    core            100000
your_username    hard   core            500000

the values are only an example !
have a look at --> man limits.conf
you have to logout and login again to get the new configuration of your limits.

ciao

---

### Post by Alex Farber on 2010-05-27
Thank you. Maybe I can add the command
ulimit -c unlimited
to some file which is executed upon login? If it is possible, what file exactly?

Also, how to write "unlimited" value to limits.conf?

---

### Post by gmargo on 2010-05-27
Try adding it to $HOME/.profile.

---

### Post by rnerwein on 2010-05-28
> **Alex Farber said:**
> Thank you. Maybe I can add the command
ulimit -c unlimited
to some file which is executed upon login? If it is possible, what file exactly?

Also, how to write "unlimited" value to limits.conf?

hi 
---> man limits.conf
[COLOR=Green]All items support the values -1, unlimited or infinity indicating no limit, except for priority and nice.[/COLOR]

it's possible to add the command "ulimit -c unlimited" into your .bashrc.
but this is not the right place !
ciao

---

