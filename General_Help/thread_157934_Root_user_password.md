---
title: "Root user password"
date: 2006-04-10
forum: General Help
---

### Post by Mario C. on 2006-04-10
hey
i can't log in as the root user using the terminal. i can use sudo fine but su doesn't like the pw i give it. there anyway to reset my root pw? or get around this problem without typing in sudo before each comand?
thanks

---

### Post by taurus on 2006-04-10
If you want to create a password for root, type this in a terminal
```

sudo passwd root

```
BUT you need to be careful when you log in as root because one wrong command can and will destroy your system...  Now you know!  ;)

---

### Post by Mario C. on 2006-04-10
haha ok. whats the safe way to log out of root?
haha thanks

---

### Post by AndyCooll on 2006-04-10
Type "exit" in the command line when you've finished. It'll drop you back in to your normal user mode. It's one of the reasons why sudo is better since it automatically drops you back to user mode.

You could also type "sudo -s". That keeps you in root privilege mode and you don't have to keep retyping sudo before each command.

:D

---

