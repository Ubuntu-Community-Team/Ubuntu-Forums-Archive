---
title: "Users &amp; PID"
date: 2009-08-31
forum: General Help
---

### Post by czepa on 2009-08-31
I got this computer on this network.
This computer has 3 users.
coal-1, coal-2 and coal-3.

I work on this computer using coal-1.

Someone, X, on my network logs through ssh using coal-2's user and password.

This some1 is able to see my PID's.

And i don't want that to happen,

and one small problem, i cant block ssh on my pc. ( its not allowed on this network ) :S

Any1 knows anything about this? :(

---

### Post by The Cog on 2009-08-31
You can prevent them from seeing your files by locking other users out of your home folder with this command:
chmod 700 ~

But I don't think there's any way to prevent them from seeing the programs you're running (and their PIDs) with the **ps** command.

---

