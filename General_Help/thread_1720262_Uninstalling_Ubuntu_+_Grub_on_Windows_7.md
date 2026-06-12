---
title: "Uninstalling Ubuntu + Grub on Windows 7"
date: 2011-04-03
forum: General Help
---

### Post by bobbymccooscoos on 2011-04-03
A while ago I decided to try out linux. I installed it the standard way (by putting in the CD and partitioning my hard drive). However, I would ow like to uninstall Ubuntu, Grub and anything associated with it. I do, however, want to keep my Windows 7 partition unharmed. How can I do that?

---

### Post by Hedgehog1 on 2011-04-03
This post is a duplicate!  Active thread is here: [http://ubuntuforums.org/showthread.php?t=1720263]("http://ubuntuforums.org/showthread.php?t=1720263")

---

### Post by rohitink on 2011-04-03
If You have installed On a separate partition then follow these steps.

If the partition is visible through My Computer.

Then Right Click Format that Drive.

Now, Restart. You will get an error b4 the boot screen. Some Grub Sort of Error.

Restart Again.

When system is booting press F8 and choose system recovery.
In system recovery select command prompt and type:

```
bootrec/fixmbr
```

Congratz, You are Free of ubnutu.

---

### Post by Bucky Ball on 2011-04-03
Welcome.

Duplicates are against forum rules. Hedgehog, Hit the Report Abuse icon and tell mods it's a duplicate NOT abusive post. Quite legit and inteded to be used this way. Will get merged quickly (generally). 

Good luck to all ... ;)

---

### Post by Elfy on 2011-04-03
Closed

---

