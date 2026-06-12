---
title: "Root password"
date: 2010-05-05
forum: General Help
---

### Post by joshklewis on 2010-05-05
I am having a problem and I'm not sure how to fix it. I know the root password, and have used it many times. Currently, I'm trying to install drivers for my printer, and am prompted for my password because it requires root privileges. However, when I type in the root password, it says that it is incorrect. I know that the password IS correct because it is the same password I use in the software center and to do updates.

What do I do? I forgot to mention that I am using Ubuntu 10.04.

---

### Post by techunit on 2010-05-05
Um it is the password you use to log-in with.

Make sure that the caps lock isn't on.

---

### Post by joshklewis on 2010-05-05
I know that it is the password I login with. That is what I'm saying, I type it in and it says it is incorrect. I know to check if the caps is on. I actually tried it with and without caps just to make sure, but still no good.

---

### Post by joshklewis on 2010-05-05
Okay, I fixed that problem. Opened terminal and just changed the password. The driver didn't even work anyway. It failed when installing, and I noticed that it says 32 bit only. I need to find one for 64 bit.

---

### Post by _0R10N on 2010-05-05
> **joshklewis said:**
> Okay, I fixed that problem. Opened terminal and just changed the password. The driver didn't even work anyway. It failed when installing, and I noticed that it says 32 bit only. I need to find one for 64 bit.

Anyway, remember that one thing is executing commands as root user and another is to type your own password to execute commands with sudoer privileges.

---

