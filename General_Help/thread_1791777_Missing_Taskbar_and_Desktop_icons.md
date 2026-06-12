---
title: "Missing Taskbar and Desktop icons"
date: 2011-06-27
forum: General Help
---

### Post by Tiagofer on 2011-06-27
I think I accidentally pressed a key and then my desktop icons and my taskbar vanished.
I've tried everything but I can't fix it. :cry:
My cursor does not move off the screen so I don't think it is a resolution problem.
I'm running Ubuntu 10.10
I've had some similar problems in the past but with a single restart of the computer the problem solved itself.
But now I can't fix this one. :cry:
Any help?

---

### Post by netherblood on 2011-06-28
Have you tried making a new user account? If it doesn't have any problem with that account then it has something to do with your configuration files.

---

### Post by Habitual on 2011-06-28
Check the trash:/// ?

---

### Post by Tiagofer on 2011-06-30
I can't create a new user account.
I don't know how to create one. :(

---

### Post by georgelab on 2011-06-30
Well,

Press Ctrl+Alt+F1 over login screen, then login as root or any other sudoer user. Then type:

**useradd username**

Then type:

**passwd username**

This will create a password for the user account.

Restart the computer and select the user you have just created... Log in using the password you've chosen before... Enjoy.

---

