---
title: "zombies"
date: 2011-05-10
forum: General Help
---

### Post by dondad on 2011-05-10
I have 2 zombies that persist across reboots. How can I get rid of them and are they really a problem? They are:
zeitgeist-datah under zeitgeist-daemon and killall underunity/sh. Both are waiting channel do_exit.

---

### Post by bowens44 on 2011-05-10
> **dondad said:**
> I have 2 zombies that persist across reboots. How can I get rid of them and are they really a problem? They are:
zeitgeist-datah under zeitgeist-daemon and killall underunity/sh. Both are waiting channel do_exit.

You have to take off their heads........

Sorry , couldn't resist.

---

### Post by cymbaline42 on 2011-05-10
There are several ways to kill a zombie, but none as satisfying as stabbing it in the head with a wooden stick.

---

### Post by WorMzy on 2011-05-10
Contrary to popular belief, you can't kill a zombie process; they can only be reaped by the parent process. You don't need to worry about them, unless, of course, they're eating up considerable amounts of RAM (which they shouldn't be). If you really can't stand having them around, killing the parent should remove the zombies.

---

