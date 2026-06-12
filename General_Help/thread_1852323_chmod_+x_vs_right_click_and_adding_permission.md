---
title: "chmod +x vs right click and adding permission"
date: 2011-09-29
forum: General Help
---

### Post by Jeepty on 2011-09-29
Hi folks,

 I was having a heck of a time installing a .bin file. I had been right clicking the file and making it executable then double clicking. The end result was a message telling me that there was no application to install it.

But, when I open up a terminal and chmod +x the same file and then run it from the terminal it installs fine.

Whats up? isn't that the same thing as doing it via the gui? Or am I missing something?

Thanks for you time.

---

### Post by CatKiller on 2011-09-30
Yes, you're missing something :)

Setting the permissions either way has exactly the same result. That wasn't the problem, though, as the error message told you. You were double-clicking the file but the system had no idea what to do with the file. Setting the permission through the Terminal and then double-clicking the file would have had exactly the same effect.

By running the file in the Terminal you explicitly told the system that you wanted to use the shell to open the file, which worked.

---

### Post by Jeepty on 2011-10-01
Ah ha! That makes sense. Thank you for the fast reply.

---

