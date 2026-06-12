---
title: "Installation with the Software Center always stuck at 70%"
date: 2009-10-31
forum: General Help
---

### Post by Shinka.S on 2009-10-31
So, when I try to install a program with the software center, it will always, always get struck at 70% (Applying Changes).

Now, the interesting thing is that, while it is stuck at 70%, the program is still installed correctly. But I can only install one program at a time, and I need to restart the computer to install new programs.

---

### Post by Shinka.S on 2009-11-07
wow...

Now I cannot even get rid of this bug by restarting the computing, it's just impossible to install anything with the software center, it's "waiting" for another process to end. I guess I'll just reinstall everything.

---

### Post by coffeecat on 2009-11-07
> **Shinka.S said:**
> I guess I'll just reinstall everything.

Before you do that.... I wonder if update-manager is autostarting and interfering with software-centre. (You can't have two processes accessing the apt backend at once.) When the software-centre gets stuck, try opening System > Administration > System Monitor. Look under the Processes tab and see if update-manager is there. If it is try ending it or killing it.

---

