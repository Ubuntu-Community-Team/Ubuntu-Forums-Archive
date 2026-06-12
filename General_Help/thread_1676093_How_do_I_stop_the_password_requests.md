---
title: "How do I stop the password requests?"
date: 2011-01-26
forum: General Help
---

### Post by jiminoregon on 2011-01-26
I'm the only one who uses or has access to my computer, so I don't need the password security that others might. Frankly, it pisses me off to have to enter my password every time I leave the computer for a few minutes, or want to make the many tweaks that are necessary to get a system going, whether it's installing software or anything else. How do I stop it?

---

### Post by dpwilson on 2011-01-26
go to system - preferences - screensaver and deselect "lock screen when screensaver is active".  I think that should do it.

---

### Post by dpwilson on 2011-01-26
You can also change the amount of time before it goes idle from the screensaver area

---

### Post by Smart Viking on 2011-01-26
system > preferences > screensaver
uncheck "lock screen when screensaver is active"

To launch like everything without password:
run "sudo visudo" in the terminal.

In the text file, enter this:
```
<username>    ALL=(ALL) ALL
```replace <username>. I don't recommend this at all.

---

### Post by hakermania on 2011-01-26
This will make your system breakable. Anybody can tell you a command and follow it and lose all your files. Be clever.

---

### Post by wojox on 2011-01-26
If you disable the sudo password you will compromise the security of your system.

You will need to search for sudoers file on the net to get achieve what you want.

---

### Post by wojox on 2011-01-26
> **Smart Viking said:**
> 
```
<username>    ALL=(ALL) ALL
```

That's normal sudo. :P

---

### Post by clhsharky on 2011-01-26
jiminoregon


> I'm the only one who uses or has access to my computer
Maybe not, if your connected to internet.


Sharky

---

