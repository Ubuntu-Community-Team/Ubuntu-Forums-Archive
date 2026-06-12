---
title: "su problem !"
date: 2011-01-15
forum: General Help
---

### Post by Killerwhalepat on 2011-01-15
hi, newb running ubuntu 10.10 here
i accidentally typed sudo chown -R (username) / 
probably messed a few things up to say the least
now every time i try to go into su mode or sudo a command i get  setgid: operation not permitted or for sudo i get sudo: must be setuid root

any solutions?

---

### Post by Smart Viking on 2011-01-15
Recently another guy accidentally did something similar. Where did you get the idea to run that command?

I would give up and reinstall the whole system.

---

### Post by Smart Viking on 2011-01-15
Recently another guy accidentally did something similar. Where did you get the idea to run that command?

I would give up and reinstall the whole system.

---

### Post by sisco311 on 2011-01-15
+1

In theory, you could boot a LiveCD and manually go through every file and directory in / and set the proper permissions, but that's very time consuming.

It's much easier and faster to backup your data and reinstall Ubuntu.

EDIT:

BTW, Welcome to the forums!

---

### Post by coffeecat on 2011-01-15
> **Killerwhalepat said:**
> probably messed a few things up to say the least

Not being unkind, but you **definitely** messed the whole system up here. I agree with the others; a reinstall is necessary.

The problem is that you have changed the ownership of every single file in the OS to yourself. Simply changing all the system files back to root ownership won't work, unfortunately. Many system files are owned by special accounts/services, not root.

---

### Post by nothingspecial on 2011-01-15
Can`t be done, I`ve tried for fun.....

..... If you do manage, post back please.

Otherwise backup and reinstall

---

