---
title: "Disable login prompt for most activities"
date: 2009-10-05
forum: General Help
---

### Post by Andy H. on 2009-10-05
My machine is in a fairly secure location and I'm not using it for any confidential applications. 

Is there a way to set Ubnu so I'm not prompted for my password for login and just about anything but application installation?

---

### Post by CatKiller on 2009-10-05
System &#8594; Administration &#8594; Login Window &#8594; Security &#8594; Enable Automatic Login.

Since you shouldn't be using *sudo* all the time anyway, that will be sufficient for your needs; you won't need to give your password for per-user tasks and will only need to give it for tasks that require root privileges.

In case you desperately need to suppress the password for other tasks, you would do so with *visudo* to edit the sudoers file. There are truly marvellous instructions for this, which this margin is too small to contain.

---

### Post by Andy H. on 2009-10-05
Thanks - I've got that enabled but it still prompts me for the passoword when I boot up.

Any other suggestions?

   -AH

---

### Post by CatKiller on 2009-10-05
Are you using wireless networking? Is it asking you to authorise access to that? There are instructions on this forum for how to deal with that, but I don't use wireless so I don't know what they are.

---

### Post by Andy H. on 2009-10-06
Yes, I'm running a wireless card for my DSL modem.  I'm occasionally asked for the password for the wireless also (it seems random), and I'm always prompted for the password when I boot up, even the "Enable Automatic Login" is checked.
 
Thanks,
 
  -AH

---

